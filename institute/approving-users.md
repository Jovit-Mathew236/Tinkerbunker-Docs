---
description: How to handle student and teacher join requests, including the approval and rejection workflow.
---

# Approving Users

Students and teachers can request to join your institute. As an institute admin, you review these requests and either approve or deny them. Until a request is acted upon, the user remains in a **Pending Approval** state and cannot access institute resources.

---

## Join Request Flow

The end-to-end flow for a join request is:

```
User submits join request
        ↓
Request appears in admin queue (Pending)
        ↓
Admin reviews the request
        ↓
   ┌────┴────┐
Approve     Deny
   │          │
   ↓          ↓
User gains   User is
access       notified
```

---

## Viewing Pending Requests

1. Navigate to **Dashboard → Join Requests** (or click the **Pending Requests** card on the dashboard).
2. The queue displays all pending requests, sorted by submission date (oldest first).

Each request shows:

| Field              | Description                                          |
| ------------------ | ---------------------------------------------------- |
| **Name**           | Full name of the requesting user.                    |
| **Email**          | Email address provided during registration.          |
| **Role**           | Whether the user is requesting as a Student or Teacher. |
| **Submitted On**   | Date and time the request was submitted.             |
| **Status**         | Always **Pending** in this view.                     |

<figure><img src="../.gitbook/assets/institute-pending-requests.png" alt="Pending Join Requests Queue"><figcaption><p>Pending join requests awaiting admin review</p></figcaption></figure>

---

## Approving a Request

1. In the join request queue, click **Approve** next to the user.
2. A confirmation dialog appears. Review the user details.
3. Click **Confirm Approval**.

Once approved:

- **Students** can browse linked courses and access classroom content.
- **Teachers** can be assigned to classrooms and manage student interactions within those classrooms.

{% hint style="info" %}
Approved users receive a notification (email or in-app) informing them that they now have access to the institute.
{% endhint %}

---

## Denying a Request

1. In the join request queue, click **Deny** next to the user.
2. Optionally, enter a reason for denial.
3. Click **Confirm Denial**.

{% hint style="warning" %}
Denied users are notified of the decision. They may submit a new join request in the future unless explicitly blocked.
{% endhint %}

---

## Bulk Actions

If you have many pending requests, you can process them in bulk:

1. Select multiple requests using the checkboxes.
2. Click **Approve Selected** or **Deny Selected** from the toolbar.
3. Confirm the bulk action.

{% hint style="info" %}
Bulk denial does not allow individual denial reasons. If you need to provide specific reasons, process those requests individually.
{% endhint %}

---

## Pending Approval State

Users in the **Pending Approval** state:

- Can log in to the platform but see a message indicating their request is under review.
- Cannot access any institute classrooms, courses, or content.
- Cannot be assigned to classrooms by the admin until approved.

{% hint style="danger" %}
Do not leave requests pending for extended periods. Users waiting too long may abandon the platform. Aim to review requests within 24-48 hours.
{% endhint %}

---

## Request History

To view previously processed requests:

1. Go to **Dashboard → Join Requests**.
2. Toggle the filter to **All** or **Processed**.
3. The history shows the action taken (Approved/Denied), the admin who processed it, and the timestamp.

---

## Related

- [Dashboard](dashboard.md)
- [Managing Classrooms](managing-classrooms.md)
