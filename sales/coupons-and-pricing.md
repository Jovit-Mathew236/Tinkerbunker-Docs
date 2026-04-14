# Coupons and Pricing

TinkerBunker supports a flexible pricing system with global seat pricing, referral codes, and partner-specific billing configurations.

---

## Global Pricing

Global pricing sets the base price per seat across the platform.

{% hint style="info" %}
Global pricing is managed by the **Super Admin**. Sales users can view pricing but cannot modify global rates.
{% endhint %}

| Field                  | Description                                |
| ---------------------- | ------------------------------------------ |
| Price per Seat (Paisa) | Base price in paisa (e.g., 100000 = ₹1000) |
| GST Percentage         | Tax rate applied (default: 18%)            |
| Effective From         | Date the pricing becomes active            |
| Effective Until        | Date the pricing expires (optional)        |

---

## Referral Codes (Coupons)

Sales users and team members with `coupon_operation` permission can create and manage referral codes that provide discounts.

### Creating a Referral Code

1. Navigate to the **Coupons** section
2. Click **Create Referral Code**
3. Fill in the details:

| Field          | Required | Description                                     |
| -------------- | -------- | ----------------------------------------------- |
| Code           | Yes      | Unique alphanumeric code                         |
| Discount Type  | Yes      | Percentage or fixed amount                       |
| Discount Value | Yes      | Discount amount (percentage or paisa)            |
| Valid From     | Yes      | Start date of validity                           |
| Valid Until    | No       | Expiry date (leave blank for no expiry)          |
| Usage Limit    | No       | Maximum number of times the code can be used     |

4. Click **Create**

{% hint style="warning" %}
Referral codes require **approval** before they become active. After creation, the code enters a pending state until approved by an authorized user.
{% endhint %}

### Referral Code Lifecycle

```
Created → Pending Approval → Approved → Active
                           → Rejected
```

### Managing Referral Codes

From the referral codes list, you can:

| Action   | Description                                      |
| -------- | ------------------------------------------------ |
| View     | See code details and usage statistics             |
| Edit     | Update discount value, validity period            |
| Approve  | Activate a pending referral code                  |
| Delete   | Remove a referral code permanently                |

---

## Calculating Price with Referral Code

When a user applies a referral code during enrollment or seat purchase:

1. The system validates the code (existence, expiry, usage limit)
2. Calculates the discounted price
3. Returns a price breakdown:

| Component        | Description                           |
| ---------------- | ------------------------------------- |
| Original Price   | Base price before discount             |
| Discount Amount  | Amount deducted by the referral code   |
| GST Amount       | Tax calculated on the discounted price |
| Final Price      | Total amount payable                   |

---

## Partner-Specific Pricing

Partners operate on a **seat-based billing model**:

### Billing Cycle

Each partner has an active billing cycle that tracks:

| Field              | Description                              |
| ------------------ | ---------------------------------------- |
| Seats Bought       | Number of seats in the current cycle     |
| Start Date         | Billing period start                      |
| End Date           | Billing period end                        |
| Due Date           | Payment due date                          |
| Price per Seat     | Rate for this cycle (in paisa)           |

### Billing Cycle Statuses

| Status     | Description                                              |
| ---------- | -------------------------------------------------------- |
| `ACTIVE`   | Current billing cycle, partner is operational            |
| `COMPLETED`| Billing cycle ended, invoice pending                     |
| `INVOICED` | Invoice generated, awaiting payment                      |
| `SUSPENDED`| Payment overdue — partner operations blocked             |

---

## Invoice Management

### Generating Invoices

Invoices are generated based on billing cycles:

1. Navigate to the partner's billing section
2. Click **Generate Invoice** (or invoices auto-generate at cycle end)
3. Select the date range
4. Review the invoice breakdown

### Invoice Details

| Field            | Description                                |
| ---------------- | ------------------------------------------ |
| Partner          | Partner being billed                        |
| Period           | Start and end dates of the billing period   |
| Base Amount      | Seat count x price per seat                 |
| GST Amount       | Tax amount (base x GST percentage)          |
| Total Amount     | Base + GST                                  |
| Status           | DRAFT / PENDING / PAID / FAILED / CANCELLED|
| Razorpay Order   | Payment gateway order reference             |

### Invoice Statuses

```
DRAFT → PENDING → PAID
                → FAILED
                → CANCELLED
```

### Downloading Invoices

- Click **Download PDF** on any invoice to get a printable copy
- Use **Download by Date Range** to export invoices for a specific period

---

## Payment Flow (Razorpay)

{% tabs %}
{% tab title="Online Payment" %}
1. Partner views their pending invoice
2. Clicks **Pay Now**
3. Razorpay checkout modal opens
4. Partner completes payment (UPI, card, net banking, etc.)
5. Payment is verified via signature validation
6. Invoice status updates to **PAID**
7. Billing cycle renews automatically
{% endtab %}

{% tab title="Webhook Processing" %}
Payments are also processed via Razorpay webhooks:

1. `payment.captured` — Payment successfully captured
2. `payment.failed` — Payment attempt failed
3. `order.paid` — Order fully paid

The system processes these events idempotently to prevent duplicate processing.
{% endtab %}

{% tab title="Reconciliation" %}
A background job runs daily to reconcile payments:

1. Fetches all payments from the last 24 hours via Razorpay API
2. Matches them against pending invoices
3. Updates invoice statuses accordingly
4. Flags any discrepancies for manual review
{% endtab %}
{% endtabs %}

---

## Billing Alerts

The platform generates billing alerts visible to partners and their institutes:

| Alert Type  | Trigger                            | Display         |
| ----------- | ---------------------------------- | --------------- |
| `INVOICED`  | Invoice generated                  | Yellow banner   |
| `SUSPENDED` | Payment overdue                    | Red banner      |
| `ACTIVE`    | Payment received, cycle renewed    | Dismissed       |

{% hint style="danger" %}
When a partner is **Suspended**, all write operations are blocked across the partner's entire hierarchy — including institutes, teachers, and students. Only resolving the outstanding payment lifts the suspension.
{% endhint %}

---

## Next Steps

- [Managing Partners](managing-partners.md) — Assign pricing to partners
- [Billing Feature Details](../features/billing.md) — Technical billing documentation
