# Managing Teams

Sales users can create teams to delegate partner management responsibilities. Team members operate under the Sales user's account with specific permission controls.

---

## Team Member Concept

A **team member** is a user who operates under a parent Sales account with delegated permissions. Team members:

- Log in with their own credentials
- See a restricted view based on assigned permissions
- Cannot manage other team members
- Cannot see the Teams or Sub Partners navigation items

```
Sales User (Primary)
  ├── Team Member A (partner_operation)
  ├── Team Member B (coupon_operation)
  └── Team Member C (partner_operation + coupon_operation)
```

---

## Available Permissions

| Permission           | Grants Access To                                  |
| -------------------- | ------------------------------------------------- |
| `partner_operation`  | Create, view, edit, and delete partners            |
| `coupon_operation`   | Create and manage referral codes and coupons       |

{% hint style="info" %}
Permissions are stored as a JSONB `controls` field on the team member entity. Multiple permissions can be assigned to a single team member.
{% endhint %}

---

## Adding a Team Member

1. Navigate to **Teams** from the sidebar
2. Click **Add Team Member**
3. Fill in the team member details:

| Field       | Required | Description                     |
| ----------- | -------- | ------------------------------- |
| Name        | Yes      | Team member's full name         |
| Email       | Yes      | Login email (must be unique)    |
| Phone       | Yes      | Contact number                  |
| Permissions | Yes      | Select one or more permissions  |

4. Click **Create**

The team member receives an invitation to set up their account.

![Add Team Member](../.gitbook/assets/add-team-member-sales.png)

{% hint style="warning" %}
Duplicate email detection is in place. If the email already exists in the system, you will receive an alert.
{% endhint %}

---

## Editing Team Member Permissions

1. Go to **Teams**
2. Click on the team member you want to edit
3. Update their permissions using the permission checkboxes
4. Click **Save**

Changes take effect immediately on the team member's next page load.

---

## Removing a Team Member

1. Navigate to **Teams**
2. Click the **Delete** action on the team member row
3. Confirm the removal

{% hint style="danger" %}
Removing a team member revokes their access immediately. Any partners they were managing remain assigned to your Sales account.
{% endhint %}

---

## Team Member Experience

When a team member logs in, their experience differs from the primary Sales user:

| Feature              | Primary Sales | Team Member |
| -------------------- | ------------- | ----------- |
| View Courses         | Yes           | Yes         |
| Manage Partners      | Yes           | If `partner_operation` granted |
| Manage Coupons       | Yes           | If `coupon_operation` granted  |
| View Teams           | Yes           | No          |
| Add Team Members     | Yes           | No          |
| View Sub Partners    | Yes           | No          |

---

## Guards and Access Control

Team member access is enforced by the `TeamMemberPermissionGuard` on the backend:

1. The guard checks if the user has the `team_member` role
2. If so, it reads the `controls` JSONB field
3. The `@RequirePermission('permission_name')` decorator specifies which permission is needed
4. Access is granted only if the required permission is present in the team member's controls

---

## Next Steps

- [Managing Partners](managing-partners.md) — Tasks your team can help with
- [Coupons and Pricing](coupons-and-pricing.md) — Manage pricing and discounts
