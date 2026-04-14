# Sales Dashboard

The Sales Dashboard is the central hub for sales personnel to manage their partners, teams, and monitor platform activity.

{% hint style="info" %}
Sales personnel are managed by **Admin Publishers**. Contact your Admin Publisher if you need access or have questions about your permissions.
{% endhint %}

---

## Overview

When you log in as a **Sales** user, your dashboard displays:

- **Approved Courses** — All live courses available for partner assignment
- **Partners List** — Partners assigned to you
- **Quick Navigation** — Access to Courses, Partners, and Teams

<figure><img src="../.gitbook/assets/sales-dashboard-overview.png" alt="Sales Dashboard Overview"><figcaption></figcaption></figure>

---

## Navigation

The Sales role has the following navigation items:

| Nav Item   | Path        | Description                        |
| ---------- | ----------- | ---------------------------------- |
| Courses    | `/courses`  | Browse all approved/live courses   |
| Partners   | `/partners` | Manage your assigned partners      |
| Teams      | `/teams`    | Manage your team members           |

{% hint style="warning" %}
The **Teams** nav item is hidden if you are logged in as a **team member** of a Sales user. Only the primary Sales account holder can manage teams.
{% endhint %}

---

## Dashboard Sections

### Approved Courses

A listing of all courses that have been approved and are available for assignment to partners. From here you can:

1. View course details (title, description, category, grade level)
2. Assign courses to your partners
3. Filter courses by category or search by name

### Partners Overview

A summary of all partners under your management, including:

- Partner name and company
- Number of institutes under each partner
- Billing status (Active, Invoiced, Overdue, Suspended)
- Seat allocation summary

---

## Team Member Access

If you are a **team member** of a Sales user, your access is controlled by the permissions granted to you:

| Permission           | Description                              |
| -------------------- | ---------------------------------------- |
| `partner_operation`  | Create, edit, and manage partners        |
| `coupon_operation`   | Create and manage referral/coupon codes  |

{% hint style="info" %}
Team members do not see the **Teams** or **Sub Partners** navigation items. Only the primary Sales user can manage team composition.
{% endhint %}

---

## Billing Banner

If any of your partners have outstanding invoices, a **Billing Banner** appears at the top of the dashboard:

- **Yellow banner** — Invoice generated, payment pending (`INVOICED` status)
- **Red banner** — Payment overdue (`SUSPENDED` status)

Partners with suspended billing cycles are blocked from write operations until payment is resolved.

---

## Next Steps

- [Managing Partners](managing-partners.md) — Add and configure partners
- [Managing Teams](managing-teams.md) — Set up your sales team
- [Coupons and Pricing](coupons-and-pricing.md) — Configure pricing and discounts
