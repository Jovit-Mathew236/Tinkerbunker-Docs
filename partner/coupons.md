---
description: Creating and managing discount coupons for schools and licensing.
---

# Coupons

Partners can create discount coupons to offer reduced pricing to schools or during promotional campaigns. Coupon management is controlled by the `coupon_operation` access flag.

---

## Viewing Coupons

1. Navigate to **Dashboard → Coupons**.
2. The coupon list displays all coupons created under your partner account.

| Column           | Description                                          |
| ---------------- | ---------------------------------------------------- |
| **Coupon Code**  | The unique code users enter to redeem the discount.  |
| **Discount**     | Percentage or flat amount off.                       |
| **Type**         | Percentage (%) or Fixed Amount.                      |
| **Usage Limit**  | Maximum number of times the coupon can be redeemed.  |
| **Used**         | Number of times the coupon has been redeemed so far. |
| **Valid From**   | Start date of the coupon validity.                   |
| **Valid Until**  | Expiration date.                                     |
| **Status**       | Active, Expired, or Disabled.                        |

<figure><img src="../.gitbook/assets/partner-coupon-list.png" alt="Coupon List"><figcaption><p>List of coupons managed under the partner account</p></figcaption></figure>

---

## Creating a Coupon

1. Go to **Dashboard → Coupons**.
2. Click **Create Coupon**.
3. Fill in the coupon details:

| Field              | Required | Description                                              |
| ------------------ | -------- | -------------------------------------------------------- |
| **Coupon Code**    | Yes      | A unique, alphanumeric code (e.g., "SUMMER2024").        |
| **Discount Type**  | Yes      | Percentage or Fixed Amount.                              |
| **Discount Value** | Yes      | The discount amount (e.g., 20 for 20% or 500 for a flat discount). |
| **Usage Limit**    | No       | Max redemptions. Leave blank for unlimited.              |
| **Valid From**     | Yes      | Start date and time.                                     |
| **Valid Until**    | Yes      | End date and time.                                       |
| **Applicable To**  | No       | Restrict to specific schools, courses, or seat plans.    |
| **Minimum Value**  | No       | Minimum order/invoice value required to use the coupon.  |

4. Click **Create**.

{% hint style="info" %}
Coupon codes are case-insensitive. "SUMMER2024" and "summer2024" are treated as the same code.
{% endhint %}

<figure><img src="../.gitbook/assets/partner-create-coupon.png" alt="Create Coupon Form"><figcaption><p>Coupon creation form with all configuration options</p></figcaption></figure>

---

## Coupon Types

{% tabs %}
{% tab title="Percentage Discount" %}
Applies a percentage reduction to the total amount.

**Example:** A 20% coupon on a 10,000 invoice reduces the payable amount to 8,000.

{% hint style="warning" %}
Percentage coupons do not have an upper cap by default. Consider setting a maximum discount amount if needed to prevent unexpectedly large discounts on high-value invoices.
{% endhint %}
{% endtab %}

{% tab title="Fixed Amount Discount" %}
Subtracts a fixed amount from the total.

**Example:** A 500 fixed discount on a 10,000 invoice reduces the payable amount to 9,500.

{% hint style="info" %}
If the fixed discount exceeds the invoice total, the payable amount is reduced to zero. No negative balances or refunds are generated.
{% endhint %}
{% endtab %}
{% endtabs %}

---

## Editing a Coupon

1. Go to **Dashboard → Coupons**.
2. Click **Edit** next to the coupon.
3. Modify the desired fields.
4. Click **Save Changes**.

{% hint style="warning" %}
You cannot change the coupon code after creation. If you need a different code, create a new coupon and disable the old one.
{% endhint %}

---

## Disabling a Coupon

To prevent a coupon from being redeemed without deleting it:

1. Click **Disable** next to the coupon.
2. Confirm the action.

Disabled coupons:

- Cannot be redeemed by anyone.
- Remain visible in the coupon list with a **Disabled** status.
- Can be re-enabled at any time.

---

## Deleting a Coupon

1. Click **Delete** next to the coupon.
2. Confirm the deletion.

{% hint style="danger" %}
Deleting a coupon is permanent. Historical redemption records are preserved in payment history, but the coupon itself cannot be recovered.
{% endhint %}

---

## `coupon_operation` Access Flag

The `coupon_operation` flag controls which team members can manage coupons:

| With Flag              | Without Flag               |
| ---------------------- | -------------------------- |
| View all coupons       | No access to Coupons section |
| Create new coupons     | Cannot view or create coupons |
| Edit existing coupons  | Cannot modify coupons |
| Disable/delete coupons | Cannot disable or delete |

---

## Coupon Redemption Tracking

Each coupon's detail view includes a **Redemptions** tab showing:

| Column          | Description                                     |
| --------------- | ----------------------------------------------- |
| **Redeemed By** | School or user who applied the coupon.          |
| **Date**        | When the coupon was redeemed.                   |
| **Invoice**     | The invoice the discount was applied to.        |
| **Discount**    | The actual discount amount applied.             |

---

## Related

- [Dashboard](dashboard.md)
- [Billing and Payments](billing-and-payments.md)
- [Managing Teams](managing-teams.md)
