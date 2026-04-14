---
description: How guardians link to student accounts and the approval process involved.
---

# Linking Students

To monitor a student's progress, you must first establish a guardian-student link. This process involves a request and approval flow to ensure both parties consent to the connection.

---

## Linkage Flow

```
Guardian sends linkage request
           ↓
Student (or institute admin) receives request
           ↓
Request is reviewed
           ↓
   ┌───────┴───────┐
Approved          Declined
   │                 │
   ↓                 ↓
Guardian gains    No link is
read access       established
```

---

## Sending a Linkage Request

1. Log in to your Guardian Dashboard.
2. Click **Link Student** (or the **+** button in the Linked Students section).
3. Enter the student's details:

| Field               | Required | Description                                     |
| ------------------- | -------- | ----------------------------------------------- |
| **Student Email**   | Yes*     | The email registered on the student's account.  |
| **Student ID**      | Yes*     | The unique student identifier within the institute. |

{% hint style="info" %}
You need to provide at least one of **Student Email** or **Student ID**. Providing both improves matching accuracy.
{% endhint %}

4. Click **Send Request**.

<figure><img src="../.gitbook/assets/guardian-link-student.png" alt="Link Student Form"><figcaption><p>Guardian sending a linkage request</p></figcaption></figure>

---

## Approval Process

Once you send a linkage request, the approval can happen in one of two ways depending on the institute's configuration:

{% tabs %}
{% tab title="Student Approval" %}
The student receives a notification and can:
- **Accept** — the guardian link is established immediately.
- **Decline** — no link is created. The guardian is notified.
{% endtab %}

{% tab title="Institute Admin Approval" %}
Some institutes require an admin to approve guardian-student links:
- The request appears in the institute admin's approval queue.
- The admin reviews and approves or denies the request.
- Both the guardian and student are notified of the outcome.
{% endtab %}
{% endtabs %}

---

## Checking Request Status

1. Go to your Guardian Dashboard.
2. Open the **Pending Linkage Requests** section.
3. Each request shows:

| Field          | Description                                          |
| -------------- | ---------------------------------------------------- |
| **Student**    | Name or identifier of the student.                   |
| **Submitted**  | Date the request was sent.                           |
| **Status**     | Pending, Approved, or Declined.                      |

{% hint style="warning" %}
Pending requests expire after a configurable period (default: 30 days). If a request expires, you must submit a new one.
{% endhint %}

---

## Approving Incoming Requests

Students can also initiate a linkage request to their guardian. If a student sends you a request:

1. You will see it in the **Pending Linkage Requests** section.
2. Click **Accept** to establish the link, or **Decline** to reject it.

---

## Unlinking a Student

If you need to remove a guardian-student link:

1. Go to **Linked Students** on your dashboard.
2. Click the **Unlink** icon next to the student.
3. Confirm the action.

{% hint style="danger" %}
Unlinking a student immediately removes your access to their progress data and test results. This action can be reversed by sending a new linkage request.
{% endhint %}

---

## Related

- [Getting Started](getting-started.md)
- [Monitoring Progress](monitoring-progress.md)
