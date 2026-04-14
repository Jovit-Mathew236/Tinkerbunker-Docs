# Switching Roles

TinkerBunker allows a single user account to hold **multiple roles** simultaneously. If you are both a Teacher at one institute and a Student at another, or if you have both Partner and Sales access, you can switch between roles without logging out.

---

## How Role Switching Works

Each role provides a different dashboard, navigation menu, and set of permissions. When you switch roles, the platform:

1. Updates the active role on your session.
2. Reloads the page.
3. Redirects you to the **dashboard** of the selected role.

Your data and progress in each role are maintained independently. Switching roles does not affect your work in any other role.

---

## Switching Roles via the Profile Menu

### Steps

1. Click your **profile avatar** or **name** in the top-right corner of the navigation bar.
2. In the dropdown menu, locate the **Role Switcher** section.
3. Your currently active role is highlighted.
4. Click on the role you want to switch to.
5. The page reloads and you are taken to the dashboard of the selected role.

<figure><img src="../.gitbook/assets/role-switcher-menu.png" alt="Role Switcher in Profile Menu"><figcaption></figcaption></figure>

{% hint style="info" %}
Only roles that have been assigned to your account appear in the role switcher. If you expect to see a role that is not listed, it may be pending approval (for institute roles) or not yet assigned.
{% endhint %}

---

## Example Scenarios

| Scenario | Roles Available | Behavior |
| --- | --- | --- |
| A teacher who is also a student at a different institute | Teacher, Student | Switch between Teacher Dashboard and Student Dashboard |
| An institute admin who is also a partner | Institute, Partner | Switch between Institute management and Partner management |
| A user who signed up and later joined an institute | Student (personal), Student (institute) | Both appear; switching changes the institute context |
| A sales team member who also creates content | Sales, Admin Creator | Switch between Sales Dashboard and Content Creator tools |

---

## What Changes When You Switch

| Aspect | Behavior |
| --- | --- |
| Dashboard | Loads the dashboard for the selected role |
| Navigation menu | Updates to show menu items relevant to the new role |
| Permissions | Scoped to the selected role's access level |
| Data context | Shows data relevant to the role (e.g., institute-specific classrooms) |
| URL | Redirects to the role's root dashboard route |

---

## Roles That Require Approval

Some roles are not immediately available after being requested:

- **Institute Student** and **Institute Teacher** roles require approval from the institute administrator.
- While pending, these roles appear in the switcher as **Pending Approval** and cannot be activated.

{% hint style="warning" %}
If a role shows as **Pending Approval**, contact the administrator of the institute you are trying to join. Once approved, the role becomes active and you can switch to it.
{% endhint %}

---

## Adding New Roles

You can acquire additional roles in the following ways:

| Method | Roles Gained |
| --- | --- |
| [Join an institute](joining-an-institute.md) | Student or Teacher (pending approval) |
| Invited by a Partner | Team Member under Partner |
| Invited by Sales | Team Member under Sales |
| Promoted by Super Admin | Any admin-level role |

---

## Next Steps

- [Join an institute to add a new role](joining-an-institute.md)
- [Return to Platform Overview](overview.md)
