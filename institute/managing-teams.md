---
description: Adding institute team members, configuring access flags, and understanding team member restrictions.
---

# Managing Teams

Institute admins can add team members who inherit a **scoped version** of the institute admin role. Each team member's access is controlled by granular access flags, ensuring they can only perform actions relevant to their responsibilities.

---

## How Team Roles Work

When you add a team member to your institute, they receive the **institute** parent role with specific access flags enabled. They do **not** get full admin access — only the operations you explicitly grant.

{% hint style="info" %}
Team members inherit a scoped version of the institute role. They can never exceed the permissions of the institute admin who created them.
{% endhint %}

---

## Adding a Team Member

1. Navigate to **Dashboard → Teams**.
2. Click **Add Team Member**.
3. Enter the team member's details:

| Field            | Required | Description                              |
| ---------------- | -------- | ---------------------------------------- |
| **Name**         | Yes      | Full name of the team member.            |
| **Email**        | Yes      | Email address (used for invitation).     |
| **Phone**        | No       | Contact number.                          |
| **Access Flags** | Yes      | One or more operation flags (see below). |

4. Review the selected access flags.
5. Click **Send Invitation**.

The team member will receive an email invitation. Once they accept and set up their account, they can access the institute dashboard with their scoped permissions.

<figure><img src="../.gitbook/assets/institute-add-team-member.png" alt="Add Team Member Form"><figcaption><p>Adding a new team member with access flag selection</p></figcaption></figure>

---

## Access Flags

The following access flags are available for institute team members:

| Flag                       | Grants Access To                                                 |
| -------------------------- | ---------------------------------------------------------------- |
| `classroom_operation`      | Create, edit, and delete classrooms. Assign teachers/students.   |
| `course_operation`         | View courses and link/unlink courses to classrooms.              |
| `course_assign_operation`  | Assign courses to the institute (if permitted by partner).       |

{% hint style="warning" %}
A team member with **no** access flags enabled will be able to log in but will see an empty dashboard with no actionable sections.
{% endhint %}

### Flag Combinations

You can combine flags to create flexible roles:

{% tabs %}
{% tab title="Classroom Manager" %}
**Flags:** `classroom_operation`

Can create and manage classrooms, assign teachers and students, but cannot manage courses independently.
{% endtab %}

{% tab title="Course Coordinator" %}
**Flags:** `course_operation`, `course_assign_operation`

Can view, link, and manage course assignments but cannot modify classroom rosters.
{% endtab %}

{% tab title="Full Operations" %}
**Flags:** `classroom_operation`, `course_operation`, `course_assign_operation`

Has access to all classroom and course management features. Closest to full admin without team management rights.
{% endtab %}
{% endtabs %}

---

## Editing a Team Member

1. Go to **Dashboard → Teams**.
2. Click the **Edit** icon next to the team member.
3. Modify their access flags or contact details.
4. Click **Save Changes**.

{% hint style="info" %}
Changes to access flags take effect on the team member's next page load or login. There is no need for them to re-accept an invitation.
{% endhint %}

---

## Removing a Team Member

1. Go to **Dashboard → Teams**.
2. Click the **Remove** icon next to the team member.
3. Confirm the removal.

{% hint style="danger" %}
Removing a team member immediately revokes their access to the institute dashboard. Any actions they previously performed (e.g., creating classrooms) are not rolled back.
{% endhint %}

---

## Team Member Restrictions

Team members are subject to the following restrictions regardless of their access flags:

- **Cannot manage other team members** — only the institute admin can add, edit, or remove team members.
- **Cannot approve or deny join requests** — user approval is reserved for the institute admin.
- **Cannot view billing or licensing** — these are managed at the partner level.
- **Cannot delete the institute** — only the primary admin or partner can perform this action.
- **Dashboard is filtered** — team members only see sections corresponding to their enabled flags.

---

## Related

- [Dashboard](dashboard.md)
- [Managing Classrooms](managing-classrooms.md)
- [Managing Courses](managing-courses.md)
