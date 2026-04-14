# Managing Sales

The Admin Publisher is responsible for managing the sales team. This includes inviting new sales personnel, managing active sales users, and overseeing partner assignments.

---

## Sales Management Dashboard

Access the sales management interface from **Sales** in the sidebar navigation.

The sales page has two main tabs:

{% tabs %}
{% tab title="Active Sales" %}
Displays all active sales personnel in a table format:

| Column    | Description                       |
| --------- | --------------------------------- |
| Name      | Sales person's full name          |
| Email     | Login email                        |
| Phone     | Contact number                     |
| Partners  | Number of partners assigned        |
| Status    | Active / Inactive                  |
| Actions   | View, Edit, Delete                 |

You can:
- Click on a sales person to view their profile and assigned partners
- Delete a sales person to revoke their access
{% endtab %}

{% tab title="Invited Sales" %}
Displays pending invitations that haven't been accepted yet:

| Column        | Description                     |
| ------------- | ------------------------------- |
| Name          | Invited person's name           |
| Email         | Invitation email                 |
| Invited Date  | When the invitation was sent     |
| Status        | Pending / Expired                |
| Actions       | Resend, Cancel                   |
{% endtab %}
{% endtabs %}

---

## Inviting Sales Personnel

1. Navigate to **Sales**
2. Click **Invite Sales**
3. Fill in the invitation form:

| Field  | Required | Description                |
| ------ | -------- | -------------------------- |
| Name   | Yes      | Full name of the invitee   |
| Email  | Yes      | Email address (must be unique) |
| Phone  | Yes      | Contact phone number       |

4. Review the invitation in the **Table Modal** (for batch invitations)
5. Click **Send Invitation**

### Invitation Flow

```
Fill Form → Review (Table Modal) → Send → Success Modal
```

![Invite Sales Flow](../../.gitbook/assets/invite-sales-flow.png)

{% hint style="warning" %}
**Duplicate Detection:** The system checks for existing users with the same email. If a duplicate is found, an alert is displayed and the invitation is not sent.
{% endhint %}

---

## Sales Person Detail View

Click on any sales person to view their full profile:

### Partner Assignments

A list of all partners managed by this sales person, including:

- Partner name and company
- Number of institutes under each partner
- Billing status
- Seat allocation

### Activity Overview

- Total partners created
- Total institutes across partners
- Active billing cycles

---

## Deleting Sales Personnel

1. Navigate to **Sales** > **Active Sales** tab
2. Click the **Delete** action on the sales person's row
3. Confirm the deletion

{% hint style="danger" %}
Deleting a sales person does not delete their assigned partners. Partners will need to be reassigned to another sales person.
{% endhint %}

---

## Publisher Dashboard: Partner Sales Table

The Admin Publisher dashboard includes a **PartnerSalesTable** widget that provides a quick overview:

| Column      | Description                         |
| ----------- | ----------------------------------- |
| Partner     | Partner name                         |
| Institute   | Number of institutes                 |
| Sales       | Assigned sales person                |
| Actions     | View, Delete                         |

This table gives you a bird's-eye view of the partner-sales relationship across the platform.

---

## Sales Role Capabilities

Each sales person you create has the following capabilities:

| Capability             | Description                                      |
| ---------------------- | ------------------------------------------------ |
| Partner Management     | Create and manage their assigned partners        |
| Team Management        | Build a team with delegated permissions           |
| Coupon Management      | Create and manage referral codes                  |
| Course Viewing         | View all approved courses                         |
| Partner Assignment     | Assign courses to their partners                  |

---

## Next Steps

- [Reviewing Courses](reviewing-courses.md) — Review and approve course submissions
- [Publishing Courses](publishing-courses.md) — Manage course visibility
