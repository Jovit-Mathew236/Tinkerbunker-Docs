# Approval System

TinkerBunker uses an approval workflow for users requesting to join institutes. Institute administrators review and approve or reject membership requests, ensuring only authorized users gain access.

---

## Overview

When a user signs up and requests to join an institute (as a student or teacher), they enter a **Pending** state. The institute admin must approve the request before the user can access institute features.

```
User registers → Selects Institute → Chooses Role (Student/Teacher)
       │
       ▼
  PENDING (awaiting approval)
       │
  ┌────┴────┐
  ▼         ▼
APPROVED  REJECTED
  │         │
  ▼         └──► Reapply (same or different institute)
Full Access
```

---

## Request Statuses

| Status      | Description                                          |
| ----------- | ---------------------------------------------------- |
| `PENDING`   | Request submitted, awaiting institute admin review   |
| `APPROVED`  | Request accepted — user gains full access            |
| `REJECTED`  | Request denied — user can reapply                    |
| `CANCELLED` | Request withdrawn by the user                        |

---

## User Experience

### Submitting a Join Request

1. User signs up for a TinkerBunker account
2. User selects an institute to join
3. User selects their role: **Student** or **Teacher**
4. The request is submitted

### Pending State

While waiting for approval, the user sees the **Pending Dashboard**:

{% tabs %}
{% tab title="Pending" %}
The dashboard shows a progress indicator:

```
Step 1: Request Submitted         [Complete]
Step 2: Institute Review           [In Progress]
Step 3: Email Notification         [Waiting]
Step 4: Full Access Granted        [Waiting]
```

The user is informed that their request is under review and they will be notified once a decision is made.
{% endtab %}

{% tab title="Approved" %}
When the institute admin approves the request:

1. The dashboard automatically detects the approval
2. Session is refreshed via `verifySession()`
3. User is redirected to their role-specific dashboard
4. Full platform access is granted based on their role
{% endtab %}

{% tab title="Rejected" %}
When the institute admin rejects the request:

1. The rejection reason is displayed
2. The user has options:
   - **Reapply** to the same institute
   - **Change institute** to apply to a different one
3. Maximum of **5 application attempts** is enforced
4. After 5 rejections, the user can no longer reapply

<figure><img src="../.gitbook/assets/pending-rejected.png" alt="Rejection with Reason"><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

### PendingApprovalGuard

The `PendingApprovalGuard` enforces route restrictions for pending users:

**Allowed routes while pending:**
- `/dashboard` — Shows the Pending Dashboard
- `/` — Home page
- `/login` — Login page
- `/forgotpassword` — Password recovery
- Static assets and API routes

**All other routes are blocked.** Attempting to navigate elsewhere redirects back to `/dashboard`.

{% hint style="warning" %}
The `PendingApprovalGuard` wraps the entire application. Pending users cannot bypass this restriction through direct URL entry or browser navigation.
{% endhint %}

---

## Institute Admin Experience

### Viewing Pending Requests

1. Log in as an institute administrator
2. Navigate to the approval management section
3. View requests filtered by:

| Filter   | Options                              |
| -------- | ------------------------------------ |
| Role     | Student, Teacher                     |
| Status   | Pending, Approved, Rejected          |

### Approving a Request

1. Review the user's profile information
2. Click **Approve**
3. The system:
   - Creates the user's Student or Teacher profile
   - Links them to the institute
   - Updates the request status to `APPROVED`
   - Records `processed_at` and `processed_by_user_id`

### Rejecting a Request

1. Review the user's profile information
2. Click **Reject**
3. Provide a **rejection reason** (required)
4. The system:
   - Updates the request status to `REJECTED`
   - Stores the rejection reason
   - Records processing details
   - Notifies the user

{% hint style="info" %}
Providing a clear rejection reason helps users understand what they need to do differently when reapplying.
{% endhint %}

---

## Reapplication Process

### Reapplying to the Same Institute

1. User views the rejection reason on their Pending Dashboard
2. Clicks **Reapply**
3. A new request is submitted
4. The `application_count` increments

### Changing Institutes

1. User clicks **Change Institute**
2. Selects a different institute
3. A new request is submitted to the new institute
4. The old request is updated

### Application Limits

| Limit               | Value | Description                              |
| -------------------- | ----- | ---------------------------------------- |
| Maximum applications | 5     | After 5 rejected attempts, user is locked out of reapplication |

{% hint style="danger" %}
After 5 failed application attempts, the user cannot submit new requests. They should contact support for assistance.
{% endhint %}

---

## Request Data

Each approval request contains:

| Field                 | Description                                 |
| --------------------- | ------------------------------------------- |
| `user_id`             | The requesting user                         |
| `institute_id`        | Target institute                            |
| `requested_role`      | `student` or `teacher`                      |
| `status`              | PENDING / APPROVED / REJECTED / CANCELLED   |
| `rejection_reason`    | Reason provided on rejection                |
| `application_count`   | Number of attempts for this user            |
| `processed_at`        | When the request was reviewed               |
| `processed_by_user_id`| Who reviewed the request                    |

---

## API Reference

| Endpoint                                            | Method | Description                      |
| --------------------------------------------------- | ------ | -------------------------------- |
| `POST /pending-requests`                            | POST   | Submit a join request            |
| `GET /pending-requests/institute/{id}`              | GET    | List requests for an institute   |
| `POST /pending-requests/{institute_id}/approve`     | POST   | Approve a request                |
| `POST /pending-requests/{institute_id}/reject`      | POST   | Reject a request                 |
| `POST /pending-requests/reapply`                    | POST   | Reapply after rejection          |
| `PATCH /pending-requests/{id}/change-institute`     | PATCH  | Switch target institute          |
| `DELETE /pending-requests/{id}`                     | DELETE | Cancel a request                 |

---

## Guards

| Guard                       | Description                                    |
| --------------------------- | ---------------------------------------------- |
| `PendingApprovalGuard`      | Frontend: blocks routes for pending users      |
| `InstituteOwnershipGuard`   | Backend: ensures only the institute admin can approve/reject |

---

## Next Steps

- [White Labeling](white-labeling.md) — Partner branding and customization
- [Role Access Matrix](role-access-matrix.md) — See which roles have approval features
