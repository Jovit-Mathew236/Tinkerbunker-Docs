---
description: Managing sub-partners under your partner account and the subpartner_operation access flag.
---

# Managing Sub Partners

Sub-partners are organizations that operate under your partner umbrella. They can manage their own set of schools, teams, and licensing — scoped to their allocated resources. Sub-partner management is controlled by the `subpartner_operation` access flag.

---

## What Are Sub Partners?

A sub-partner is a downstream partner entity. The hierarchy is:

```
Partner (you)
  ├── Sub Partner A
  │     ├── School 1
  │     └── School 2
  ├── Sub Partner B
  │     └── School 3
  └── Directly managed schools
        ├── School 4
        └── School 5
```

Sub-partners have their own dashboard and can manage schools assigned to them, but they operate within the boundaries you define (seat allocations, course availability, etc.).

---

## Viewing Sub Partners

1. Navigate to **Dashboard → Sub Partners**.
2. The list displays all sub-partners under your account.

| Column              | Description                                         |
| ------------------- | --------------------------------------------------- |
| **Sub Partner Name**| Organization name.                                  |
| **Contact**         | Primary contact person.                             |
| **Schools**         | Number of schools managed by this sub-partner.      |
| **Seats Allocated** | Total seats allocated to this sub-partner.          |
| **Status**          | Active or Suspended.                                |

<figure><img src="../.gitbook/assets/partner-sub-partner-list.png" alt="Sub Partner List"><figcaption><p>List of sub-partners under your partner account</p></figcaption></figure>

---

## Adding a Sub Partner

1. Go to **Dashboard → Sub Partners**.
2. Click **Add Sub Partner**.
3. Fill in the sub-partner details:

| Field                  | Required | Description                                    |
| ---------------------- | -------- | ---------------------------------------------- |
| **Organization Name**  | Yes      | Name of the sub-partner organization.          |
| **Contact Name**       | Yes      | Primary contact person.                        |
| **Contact Email**      | Yes      | Email for the sub-partner admin account.       |
| **Contact Phone**      | No       | Phone number.                                  |
| **Seat Allocation**    | Yes      | Number of seats to allocate to this sub-partner.|

4. Click **Create Sub Partner**.

An invitation is sent to the contact email. The sub-partner admin must accept and set up their account.

{% hint style="info" %}
Seats allocated to a sub-partner are deducted from your total available seats. Plan allocations carefully to avoid over-commitment.
{% endhint %}

---

## `subpartner_operation` Access Flag

The `subpartner_operation` flag controls who can manage sub-partners. This flag is relevant in two contexts:

### For Partner Team Members

When adding team members to your partner account (see [Managing Teams](managing-teams.md)), enabling `subpartner_operation` grants them:

- View the sub-partner list.
- Add new sub-partners.
- Edit sub-partner details and allocations.
- Suspend or reactivate sub-partners.

### Without the Flag

Team members **without** `subpartner_operation`:

- Cannot see the Sub Partners section in the dashboard.
- Cannot access any sub-partner management features.

{% hint style="warning" %}
Only grant `subpartner_operation` to trusted team members who need to manage the sub-partner hierarchy. This flag gives significant control over resource distribution.
{% endhint %}

---

## Editing a Sub Partner

1. Go to **Dashboard → Sub Partners**.
2. Click **Edit** next to the sub-partner.
3. Update the desired fields (name, contact info, seat allocation).
4. Click **Save Changes**.

### Adjusting Seat Allocation

- **Increasing** seats: deducts from your available pool.
- **Decreasing** seats: only possible if the sub-partner's active usage is below the new limit.

{% hint style="danger" %}
You cannot reduce a sub-partner's seat allocation below their current active seat count. The sub-partner must release seats (by removing students or suspending schools) before you can lower the allocation.
{% endhint %}

---

## Suspending a Sub Partner

1. Open the sub-partner detail view.
2. Click **Suspend**.
3. Confirm the action.

When suspended:

- The sub-partner admin and their team lose dashboard access.
- All schools under the sub-partner are also suspended.
- Seat allocations are frozen but not released back to your pool until you explicitly reclaim them.

---

## Removing a Sub Partner

{% hint style="danger" %}
Removing a sub-partner is a destructive action. All schools under the sub-partner must be reassigned or deleted before removal is allowed.
{% endhint %}

1. Ensure the sub-partner has no active schools.
2. Go to **Dashboard → Sub Partners**.
3. Click **Remove** next to the sub-partner.
4. Confirm the removal.

---

## Related

- [Dashboard](dashboard.md)
- [Managing Teams](managing-teams.md)
- [Seats and Licensing](seats-and-licensing.md)
