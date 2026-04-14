---
description: Adding partner team members, configuring access flags, and understanding team member restrictions.
---

# Managing Teams

Partners can add team members who inherit a **scoped version** of the partner role. Each team member's capabilities are determined by the access flags you assign, ensuring fine-grained control over who can do what.

---

## How Team Roles Work

When you add a team member, they receive the **partner** parent role with specific access flags enabled. They do not get full partner access — only the operations you explicitly grant.

{% hint style="info" %}
Team members inherit a scoped version of the partner role. They can never exceed the permissions of the partner admin who created them.
{% endhint %}

---

## Adding a Team Member

1. Navigate to **Dashboard → Teams**.
2. Click **Add Team Member**.
3. Enter the member's details:

| Field            | Required | Description                              |
| ---------------- | -------- | ---------------------------------------- |
| **Name**         | Yes      | Full name of the team member.            |
| **Email**        | Yes      | Email address (used for invitation).     |
| **Phone**        | No       | Contact number.                          |
| **Access Flags** | Yes      | One or more operation flags (see below). |

4. Review the access flag selection.
5. Click **Send Invitation**.

<figure><img src="../.gitbook/assets/partner-add-team-member.png" alt="Add Partner Team Member"><figcaption><p>Adding a partner team member with access flag selection</p></figcaption></figure>

---

## Access Flags

The following access flags are available for partner team members:

| Flag                       | Grants Access To                                                    |
| -------------------------- | ------------------------------------------------------------------- |
| `school_operation`         | Add, edit, suspend, and manage schools (institutes).                |
| `subpartner_operation`     | Add, edit, suspend, and manage sub-partners.                        |
| `seat_operation`           | Manage seat allocations and licensing for schools and sub-partners.  |
| `classroom_operation`      | Manage classrooms within schools (create, edit, assign).            |
| `course_operation`         | View and manage course assignments across schools.                  |
| `course_assign_operation`  | Assign new courses to schools.                                      |
| `partner_operation`        | Manage partner-level settings and configurations.                   |
| `coupon_operation`         | Create, edit, and manage discount coupons.                          |
| `price_operation`          | View and manage pricing configurations.                             |

{% hint style="warning" %}
A team member with **no** access flags enabled will be able to log in but will see an empty dashboard with no actionable sections.
{% endhint %}

---

## Flag Combinations

Combine flags to create practical roles:

{% tabs %}
{% tab title="School Manager" %}
**Flags:** `school_operation`, `classroom_operation`

Can manage schools and their classrooms. Cannot handle billing, licensing, or sub-partners.
{% endtab %}

{% tab title="Operations Lead" %}
**Flags:** `school_operation`, `seat_operation`, `course_operation`, `course_assign_operation`

Can manage schools, handle seat allocations, and manage courses. No access to sub-partners or coupons.
{% endtab %}

{% tab title="Finance Manager" %}
**Flags:** `seat_operation`, `coupon_operation`, `price_operation`

Can manage licensing, coupons, and pricing. No access to schools or sub-partners directly.
{% endtab %}

{% tab title="Full Operations" %}
**Flags:** All flags enabled.

Has access to every section. Closest to full partner access without team management rights.
{% endtab %}
{% endtabs %}

---

## Editing a Team Member

1. Go to **Dashboard → Teams**.
2. Click the **Edit** icon next to the team member.
3. Update their access flags or contact details.
4. Click **Save Changes**.

{% hint style="info" %}
Access flag changes take effect on the team member's next page load or login. No re-invitation is needed.
{% endhint %}

---

## Removing a Team Member

1. Go to **Dashboard → Teams**.
2. Click the **Remove** icon next to the team member.
3. Confirm the removal.

{% hint style="danger" %}
Removing a team member immediately revokes their access. Actions they previously performed are not rolled back.
{% endhint %}

---

## Team Member Restrictions

Regardless of access flags, team members are subject to these restrictions:

- **Cannot manage other team members** — only the primary partner admin can add, edit, or remove team members.
- **Cannot access billing or payment history** — billing is reserved for the primary partner admin.
- **Cannot delete the partner account** — reserved for the primary admin.
- **Dashboard is filtered** — only sections matching enabled flags are visible.
- **Cannot exceed parent permissions** — a team member can never perform actions the partner admin cannot.

---

## Related

- [Dashboard](dashboard.md)
- [Managing Schools](managing-schools.md)
- [Managing Sub Partners](managing-sub-partners.md)
- [Seats and Licensing](seats-and-licensing.md)
