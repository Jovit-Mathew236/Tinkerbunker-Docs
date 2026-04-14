---
description: Billing banner, invoice management, payment history, and overdue tracking for partners.
---

# Billing and Payments

The Billing section gives you complete visibility into your financial obligations — invoices, payment history, and overdue balances. A persistent billing banner on the dashboard ensures you never miss a payment deadline.

---

## Billing Banner

The billing banner appears at the top of the Partner Dashboard whenever there are outstanding invoices:

| Banner Color | Meaning                                                       |
| ------------ | ------------------------------------------------------------- |
| **Yellow**   | You have invoices that are due but not yet past the due date. |
| **Red**      | One or more invoices are overdue (past the due date).         |

<figure><img src="../.gitbook/assets/partner-billing-banner.png" alt="Billing Banner"><figcaption><p>Red billing banner indicating overdue invoices</p></figcaption></figure>

The banner displays:

- **Total Invoiced** — sum of all unpaid invoices.
- **Total Overdue** — sum of invoices past their due date.

Clicking the banner navigates to the Billing page.

{% hint style="danger" %}
Overdue balances may result in service restrictions. Schools under your account could lose access if invoices remain unpaid beyond the grace period. Settle overdue invoices promptly.
{% endhint %}

---

## Invoice List

1. Navigate to **Dashboard → Billing**.
2. The invoice list shows all invoices:

| Column           | Description                                      |
| ---------------- | ------------------------------------------------ |
| **Invoice ID**   | Unique identifier for the invoice.               |
| **Date Issued**  | When the invoice was generated.                  |
| **Due Date**     | Payment deadline.                                |
| **Amount**       | Total amount due.                                |
| **Status**       | Paid, Unpaid, Overdue, or Partially Paid.        |
| **Actions**      | View details, download PDF, or make a payment.   |

### Filtering Invoices

Use the filters at the top of the list:

- **Status** — filter by Paid, Unpaid, Overdue, or All.
- **Date Range** — filter by issue date or due date range.
- **Amount Range** — filter by invoice amount.

---

## Invoice Detail View

Click on any invoice to see:

- **Line Items** — breakdown of charges (seats, courses, services).
- **Payments Applied** — any partial or full payments already made.
- **Remaining Balance** — outstanding amount.
- **Notes** — any notes from the platform administrator.

<figure><img src="../.gitbook/assets/partner-invoice-detail.png" alt="Invoice Detail"><figcaption><p>Detailed view of an invoice with line items</p></figcaption></figure>

---

## Making a Payment

{% tabs %}
{% tab title="Online Payment" %}
1. Open the invoice detail view.
2. Click **Pay Now**.
3. Select a payment method (credit card, bank transfer, or wallet).
4. Enter payment details and confirm.
5. A receipt is generated immediately upon successful payment.
{% endtab %}

{% tab title="Offline Payment" %}
If you make a payment outside the platform (e.g., bank transfer):
1. Open the invoice detail view.
2. Click **Record Payment**.
3. Enter the payment amount, date, and reference number.
4. Upload proof of payment (optional but recommended).
5. Submit for verification.

{% hint style="info" %}
Offline payments require admin verification before the invoice status is updated. This may take 1-3 business days.
{% endhint %}
{% endtab %}
{% endtabs %}

---

## Payment History

To view your complete payment history:

1. Go to **Dashboard → Billing → Payment History** (or access from your **Profile**).
2. The history displays:

| Column             | Description                                     |
| ------------------ | ----------------------------------------------- |
| **Payment ID**     | Unique payment identifier.                      |
| **Date**           | When the payment was made.                      |
| **Amount**         | Payment amount.                                 |
| **Method**         | Payment method used.                            |
| **Invoice**        | The invoice this payment was applied to.        |
| **Status**         | Confirmed, Pending Verification, or Failed.     |

{% hint style="info" %}
Payment history is also accessible from your **Profile** page for quick reference.
{% endhint %}

---

## Overdue Tracking

The system automatically tracks overdue invoices and applies the following escalation:

| Stage            | Trigger                           | Action                                         |
| ---------------- | --------------------------------- | ---------------------------------------------- |
| **Reminder**     | 3 days before due date            | Email reminder sent to partner admin.          |
| **Due**          | On the due date                   | Yellow banner appears on dashboard.            |
| **Overdue**      | 1 day past due date               | Red banner appears. Email notification sent.   |
| **Grace Period** | 7-14 days past due (configurable) | Warning of potential service restriction.      |
| **Restriction**  | Beyond grace period               | Access to certain features may be restricted.  |

{% hint style="warning" %}
The grace period duration is set by the platform administrator and may vary. Check your partner agreement for specific terms.
{% endhint %}

---

## Downloading Invoices

To download an invoice as a PDF:

1. From the invoice list, click the **Download** icon next to the invoice.
2. Alternatively, open the invoice detail view and click **Download PDF**.

---

## Related

- [Dashboard](dashboard.md)
- [Seats and Licensing](seats-and-licensing.md)
- [Coupons](coupons.md)
