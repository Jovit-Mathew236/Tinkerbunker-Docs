# Managing Courses (Super Admin)

The Super Admin has unrestricted access to all courses across the platform, regardless of status or creator. This guide covers course management from the Super Admin perspective.

---

## Overview

As a Super Admin, you have full visibility and control over every course in the system:

| Capability                | Description                                      |
| ------------------------- | ------------------------------------------------ |
| View all courses          | See courses in any status (draft through archived)|
| Change any status         | Transition a course to any valid status           |
| Manage categories         | CRUD operations on course categories              |
| Manage global pricing     | Set platform-wide seat pricing                    |
| Delete any course         | Remove courses regardless of status               |

---

## Navigation

| Nav Item    | Path           | Description                      |
| ----------- | -------------- | -------------------------------- |
| Courses     | `/courses`     | View and manage all courses      |
| Categories  | `/categories`  | Manage course categories         |

---

## Course Tabs

| Tab              | Shows                                      |
| ---------------- | ------------------------------------------ |
| **All Courses**  | Every course across all statuses           |
| **Categories**   | Browse courses organized by category       |

---

## Viewing All Courses

1. Navigate to **Courses**
2. The **All Courses** tab displays every course in the system
3. Use filters to narrow by:
   - Status (Draft, Pending Review, Approved, etc.)
   - Category
   - Creator
   - Date range

---

## Status Management

The Super Admin can change a course to **any** status:

| From (Any Status) | To                    | Use Case                              |
| ------------------ | --------------------- | ------------------------------------- |
| Any                | `DRAFT`               | Reset course to draft state           |
| Any                | `PENDING_REVIEW`      | Push to review queue                  |
| Any                | `APPROVED`            | Directly approve a course             |
| Any                | `CHANGES_REQUESTED`   | Request changes from creator          |
| Any                | `ARCHIVED`            | Archive an old course                 |

{% hint style="warning" %}
Use direct status changes carefully. Bypassing the normal review workflow should only be done in exceptional circumstances.
{% endhint %}

---

## Global Pricing

Super Admins manage the platform-wide pricing configuration:

1. Navigate to the **Pricing** section
2. Configure:

| Field                  | Description                                |
| ---------------------- | ------------------------------------------ |
| Price per Seat (Paisa) | Base price for each seat                   |
| GST Percentage         | Tax rate (default: 18%)                    |
| Effective From         | When the pricing takes effect              |
| Effective Until        | When the pricing expires (optional)        |

![Global Pricing Configuration](../../.gitbook/assets/global-pricing.png)

{% hint style="info" %}
Pricing changes apply to new billing cycles. Existing cycles retain their original pricing until renewal.
{% endhint %}

---

## Course Oversight

### Monitoring Course Quality

Use the All Courses view to monitor:

- Courses stuck in review for too long
- Courses with frequent rejections
- Course categories that need more content
- Pricing and visibility consistency

### Bulk Operations

From the course list:

- Filter by status to find courses needing attention
- Sort by date to see the most recent changes
- Search by title or category

---

## Next Steps

- [Managing Categories](managing-categories.md) — Create and organize course categories
