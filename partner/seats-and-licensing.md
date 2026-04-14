---
description: Managing seat allocations and licensing for institutes and sub-partners.
---

# Seats and Licensing

Seats represent licensed access slots for students. As a partner, you manage how seats are distributed across your schools and sub-partners. The `seat_operation` access flag controls who on your team can manage licensing.

---

## Understanding Seats

| Term                   | Definition                                                 |
| ---------------------- | ---------------------------------------------------------- |
| **Total Seats**        | The total number of seats in your partner account.         |
| **Allocated Seats**    | Seats assigned to schools or sub-partners.                 |
| **Available Seats**    | Total minus allocated. The pool you can still distribute.  |
| **Active Seats**       | Seats currently occupied by enrolled students.             |
| **Unused Seats**       | Allocated but not yet occupied by students.                |

{% hint style="info" %}
A student occupies one seat. When a student is enrolled in a school, one seat is consumed from that school's allocation.
{% endhint %}

---

## Seat Overview

1. Navigate to **Dashboard → Seats**.
2. The overview page displays:

<figure><img src="../.gitbook/assets/partner-seat-overview.png" alt="Seat Overview"><figcaption><p>Partner seat allocation overview</p></figcaption></figure>

- **Total / Allocated / Available** — high-level seat distribution.
- **By School** — table showing each school's allocation, active usage, and utilization rate.
- **By Sub Partner** — table showing each sub-partner's allocation and downstream distribution.

---

## Allocating Seats to a School

1. Go to **Dashboard → Seats**.
2. In the **By School** table, click **Edit** next to the school.
3. Enter the new seat allocation.
4. Click **Save**.

Alternatively, when adding a new school:

1. During the school creation form, set the **Seat Allocation** field.
2. The allocation is applied immediately upon creation.

{% hint style="warning" %}
You cannot allocate more seats than your available pool. If you need additional seats, contact your platform administrator or adjust existing allocations.
{% endhint %}

---

## Allocating Seats to a Sub Partner

1. Go to **Dashboard → Seats** or **Dashboard → Sub Partners**.
2. Click **Edit** next to the sub-partner.
3. Adjust the seat allocation.
4. Click **Save**.

Sub-partners then distribute their allocated seats to their own schools.

{% hint style="danger" %}
Reducing a sub-partner's allocation below their current active usage is not allowed. They must release seats first.
{% endhint %}

---

## `seat_operation` Access Flag

The `seat_operation` flag determines which team members can manage licensing:

| With Flag       | Without Flag          |
| --------------- | --------------------- |
| View seat overview | No access to Seats section |
| Allocate seats to schools | Cannot view or modify allocations |
| Allocate seats to sub-partners | Cannot see seat usage data |
| Adjust existing allocations | |

{% hint style="info" %}
Combine `seat_operation` with `school_operation` to allow a team member to both manage schools and their licensing in one workflow.
{% endhint %}

---

## Monitoring Utilization

The Seats page provides utilization metrics:

| Metric                | Description                                               |
| --------------------- | --------------------------------------------------------- |
| **Utilization Rate**  | (Active Seats / Allocated Seats) as a percentage.         |
| **Underutilized**     | Schools with utilization below 50% (highlighted in yellow).|
| **Near Capacity**     | Schools with utilization above 90% (highlighted in orange).|
| **At Capacity**       | Schools where active seats equal allocated seats (red).   |

{% hint style="warning" %}
Schools at capacity cannot enroll new students until additional seats are allocated or existing students are removed.
{% endhint %}

---

## Reclaiming Seats

If a school has unused seats you want to redistribute:

1. Go to **Dashboard → Seats**.
2. Click **Edit** next to the school.
3. Reduce the allocation (must remain at or above active seat count).
4. Click **Save**.

The freed seats return to your available pool and can be reallocated to other schools or sub-partners.

---

## Seat History

To view historical seat changes:

1. Go to **Dashboard → Seats**.
2. Click **View History**.
3. The log shows all allocation changes with timestamps, the user who made the change, and the before/after values.

---

## Related

- [Dashboard](dashboard.md)
- [Managing Schools](managing-schools.md)
- [Managing Sub Partners](managing-sub-partners.md)
- [Billing and Payments](billing-and-payments.md)
