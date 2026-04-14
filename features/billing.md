# Billing

TinkerBunker integrates with **Razorpay** for payment processing and provides a comprehensive billing system for partner-based seat management, invoicing, and course payments.

---

## Billing Architecture

```
Global Pricing (Super Admin)
        │
        ▼
Partner Seat Pool
   ├── Billing Cycles (monthly/custom)
   ├── Invoices (per cycle)
   ├── Payments (Razorpay)
   └── Seat Allocations → Institutes
```

---

## Seat-Based Billing

Partners operate on a seat-based billing model where they purchase seats and allocate them to institutes.

### Seat Pool

Each partner has a seat pool:

| Field             | Description                              |
| ----------------- | ---------------------------------------- |
| `total_seats`     | Total seats purchased by the partner     |
| `allocated_seats` | Seats distributed to institutes          |
| `free_seats`      | Unallocated seats available              |

### Purchasing Seats

1. Partner or Sales agent navigates to billing
2. Clicks **Purchase Seats**
3. Enters the number of seats needed
4. An invoice is generated based on the current pricing

{% hint style="info" %}
Seat purchases require `seat_operation` permission. This is available to partners and team members with the permission granted.
{% endhint %}

### Allocating Seats

1. Navigate to the partner's **Institutes** section
2. Select an institute
3. Click **Allocate Seats**
4. Enter the number of seats
5. Seats move from the partner's free pool to the institute

### Deallocating Seats

Seats can be returned from an institute to the partner's free pool:

1. Select the institute
2. Click **Deallocate Seats**
3. Enter the number to deallocate
4. Seats return to the partner's free pool

---

## Billing Cycles

Each partner has billing cycles that track their seat subscriptions:

### Cycle Fields

| Field               | Description                              |
| ------------------- | ---------------------------------------- |
| `seats_bought`      | Number of seats in the cycle             |
| `start_date`        | Billing period start                      |
| `end_date`          | Billing period end                        |
| `due_date`          | Payment due date                          |
| `price_per_seat`    | Rate for this cycle (in paisa)           |
| `status`            | Current cycle status                      |

### Cycle Statuses

```
ACTIVE → COMPLETED → INVOICED → SUSPENDED
```

| Status      | Description                                                |
| ----------- | ---------------------------------------------------------- |
| `ACTIVE`    | Current billing cycle, partner operational                 |
| `COMPLETED` | Billing cycle ended, invoice pending generation            |
| `INVOICED`  | Invoice generated, awaiting payment                        |
| `SUSPENDED` | Payment overdue — all write operations blocked             |

{% hint style="danger" %}
**Suspension Cascade:** When a partner is suspended, the `SuspendedPartnerGuard` blocks write operations for the partner and their entire hierarchy: institutes, teachers, and students. Each role receives a specific error message explaining the billing issue.
{% endhint %}

---

## Invoicing

### Invoice Fields

| Field                | Description                              |
| -------------------- | ---------------------------------------- |
| `partner_id`         | Partner being billed                      |
| `period_start`       | Invoice period start date                 |
| `period_end`         | Invoice period end date                   |
| `base_amount_paisa`  | Seats x price per seat                   |
| `gst_percentage`     | Tax rate (default 18%)                   |
| `gst_amount_paisa`   | Tax amount                               |
| `total_amount_paisa` | Base + GST                               |
| `razorpay_order_id`  | Payment gateway order reference          |
| `razorpay_payment_id`| Payment transaction ID                   |
| `status`             | Invoice status                           |
| `lines`              | Line items (seat details)                |

### Invoice Statuses

```
DRAFT → PENDING → PAID
                → FAILED
                → CANCELLED
```

| Status      | Description                                 |
| ----------- | ------------------------------------------- |
| `DRAFT`     | Invoice created, not yet finalized          |
| `PENDING`   | Invoice sent, awaiting payment              |
| `PAID`      | Payment received and verified               |
| `FAILED`    | Payment attempt failed                      |
| `CANCELLED` | Invoice voided                              |

### Generating Invoices

Invoices can be generated:

1. **Automatically** — At the end of a billing cycle
2. **Manually** — By date range via `POST /billing/invoices/by-date-range`

### Downloading Invoices

- **Single invoice:** `GET /billing/invoices/{id}/download` (PDF)
- **Date range:** `GET /billing/invoices/by-date-range/download` (PDF)

---

## Razorpay Integration

### Payment Flow

{% tabs %}
{% tab title="Course Payments" %}
For paid public courses:

1. Student clicks **Enroll** on a paid course
2. System creates a Razorpay order
3. Razorpay checkout modal opens
4. Student selects payment method (UPI, Card, Net Banking, Wallets)
5. Payment is processed by Razorpay
6. Signature is verified: `HMAC-SHA256(order_id|payment_id, secret)`
7. Enrollment record is created with Razorpay references
8. Student gains course access

**Enrollment record includes:**
- `razorpay_order_id`
- `razorpay_payment_id`
{% endtab %}

{% tab title="Invoice Payments" %}
For partner billing:

1. Partner views pending invoice
2. Clicks **Pay Now**
3. System calls `createPaymentOrder(invoiceId)`:
   - Returns `{ order_id, amount, currency: "INR", key_id }`
4. Razorpay checkout modal opens
5. Partner completes payment
6. System calls `verifyPayment`:
   - Validates `HMAC-SHA256(order_id|payment_id, secret)`
7. Invoice status updates to `PAID`
8. Billing cycle renews
9. Suspension is lifted (if applicable)
{% endtab %}

{% tab title="Webhook Processing" %}
Razorpay sends webhook events for asynchronous payment processing:

| Event              | Action                                      |
| ------------------ | ------------------------------------------- |
| `payment.captured` | Payment successfully captured → Mark paid   |
| `payment.failed`   | Payment failed → Mark as failed             |
| `order.paid`       | Order fully paid → Confirm and process      |

**Webhook endpoint:** `POST /billing/webhooks/razorpay`

Webhook signatures are verified before processing. Events are processed idempotently to prevent duplicate actions.

**Processing creates a Payment record:**

| Field                  | Description                           |
| ---------------------- | ------------------------------------- |
| `razorpay_payment_id`  | Razorpay transaction ID               |
| `razorpay_order_id`    | Razorpay order ID                     |
| `amount`               | Payment amount in paisa               |
| `currency`             | Currency (INR)                        |
| `status`               | CREATED / AUTHORIZED / CAPTURED / etc.|
| `source`               | WEBHOOK / RECONCILIATION / MANUAL     |
{% endtab %}

{% tab title="Reconciliation" %}
A daily background job reconciles payments:

1. Fetches all Razorpay payments from the last 24 hours
2. Matches against pending invoices and orders
3. Updates payment statuses
4. Triggers seat renewal for newly confirmed payments
5. Sends confirmation emails
6. Flags discrepancies for manual review

This ensures no payments are missed even if webhooks fail.
{% endtab %}
{% endtabs %}

---

## Payment Statuses

| Status         | Description                              |
| -------------- | ---------------------------------------- |
| `CREATED`      | Payment record created                   |
| `AUTHORIZED`   | Payment authorized by gateway            |
| `CAPTURED`     | Payment captured and funds received      |
| `REFUNDED`     | Payment refunded to the payer            |
| `FAILED`       | Payment attempt failed                   |

---

## Billing Alerts

The platform generates visual alerts for billing events:

| Alert Type   | Display        | Trigger                          |
| ------------ | -------------- | -------------------------------- |
| `INVOICED`   | Yellow banner  | Invoice generated, payment due   |
| `SUSPENDED`  | Red banner     | Payment overdue                  |
| `ACTIVE`     | No banner      | Payment received, cycle active   |

Alerts track which users have read them via the `read_by` array.

---

## Global Pricing (Super Admin)

Super Admins configure platform-wide pricing:

| Field                  | Description                            |
| ---------------------- | -------------------------------------- |
| `price_per_seat_paisa` | Base seat price (e.g., 100000 = ₹1000)|
| `gst_percentage`       | Tax rate (default: 18%)               |
| `effective_from`       | When pricing becomes active           |
| `effective_until`      | When pricing expires                  |

{% hint style="info" %}
Pricing changes apply only to new billing cycles. Active cycles retain their original pricing until renewal.
{% endhint %}

---

## Refunds

The platform supports refund processing through Razorpay:

1. Admin initiates a refund via `refundPayment()`
2. Razorpay API processes the refund
3. Payment status updates to `REFUNDED`
4. The refund amount is returned to the payer's original payment method

---

## API Reference

| Endpoint                                    | Method | Description                    |
| ------------------------------------------- | ------ | ------------------------------ |
| `POST /billing/seats/purchase`              | POST   | Purchase seats for a partner   |
| `POST /billing/seats/allocate`              | POST   | Allocate seats to an institute |
| `POST /billing/seats/deallocate`            | POST   | Deallocate seats               |
| `GET /billing/seats/pool/{partnerId}`       | GET    | Get partner's seat pool        |
| `GET /billing/seats/allocations/{partnerId}`| GET    | Get institute allocations      |
| `GET /billing/invoices/partner/{partnerId}` | GET    | Get partner's invoices         |
| `POST /billing/invoices/{id}/pay`           | POST   | Initiate payment               |
| `POST /billing/invoices/payment/verify`     | POST   | Verify payment signature       |
| `GET /billing/invoices/{id}/download`       | GET    | Download invoice PDF           |
| `POST /billing/webhooks/razorpay`           | POST   | Razorpay webhook handler       |

---

## Next Steps

- [Coupons and Pricing](../sales/coupons-and-pricing.md) — Sales-side pricing management
- [Approval System](approval-system.md) — Institute approval workflow
