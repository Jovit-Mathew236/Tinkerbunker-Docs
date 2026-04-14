# Managing Teams (Admin Creator)

Admin Creators can build teams to collaborate on course creation. Team members operate under the creator's account with specific permissions.

---

## Overview

Team members for Admin Creators have focused permissions related to course operations. This allows you to delegate course creation tasks while maintaining control over your content.

{% hint style="info" %}
Team members log in with their own credentials but operate under your Admin Creator account's scope.
{% endhint %}

---

## Available Permissions

| Permission          | Grants Access To                                    |
| ------------------- | --------------------------------------------------- |
| `course_operation`  | Create, edit, and manage courses under the creator  |

{% hint style="info" %}
Unlike Sales or Partner team members, Admin Creator team members have only one available permission: `course_operation`. This gives them full access to course creation workflows.
{% endhint %}

---

## Adding a Team Member

1. Navigate to **Teams** from the sidebar
2. Click **Add Team Member**
3. Fill in the required details:

| Field       | Required | Description                     |
| ----------- | -------- | ------------------------------- |
| Name        | Yes      | Team member's full name         |
| Email       | Yes      | Login email (must be unique)    |
| Phone       | Yes      | Contact number                  |
| Permissions | Yes      | Select `course_operation`       |

4. Click **Create**

The team member receives an invitation to join and set up their account.

![Add Creator Team Member](../../.gitbook/assets/add-team-member-creator.png)

---

## Editing Team Members

1. Go to **Teams**
2. Click on the team member to edit
3. Update permissions using the **Edit Team Member Modal**
4. Click **Save**

---

## Removing a Team Member

1. Navigate to **Teams**
2. Click the **Delete** action on the team member row
3. Confirm the removal

{% hint style="danger" %}
Removing a team member immediately revokes their access. Courses they created remain associated with your Admin Creator account.
{% endhint %}

---

## Team Member Experience

When a team member with `course_operation` logs in:

| Feature              | Primary Creator | Team Member |
| -------------------- | --------------- | ----------- |
| View Courses         | Yes             | Yes         |
| Create Courses       | Yes             | Yes (if `course_operation`) |
| Edit Courses         | Yes             | Yes (if `course_operation`) |
| Delete Courses       | Yes             | Yes (if `course_operation`) |
| Submit for Review    | Yes             | Yes (if `course_operation`) |
| View Teams           | Yes             | No          |
| Add Team Members     | Yes             | No          |

---

## Access Control

Team member access is enforced through:

1. **`TeamMemberPermissionGuard`** — Checks the `controls` JSONB field on the team member entity
2. **`@RequirePermission('course_operation')`** — Decorator on course endpoints
3. **Frontend filtering** — Teams nav item is hidden for team members

The `team_type` for Admin Creator team members is set to `admin_creator`, and their `parent_id` links to the primary Admin Creator's account.

---

## Next Steps

- [Creating Courses](creating-courses.md) — Delegate course creation to team members
- [Managing Content](managing-content.md) — Collaborate on content updates
