# Managing Partners

Partners are organizations that operate white-labeled instances of TinkerBunker. As a Sales user, you are responsible for creating, configuring, and managing your assigned partners.

---

## Partner Hierarchy

```
Sales Agent
  └── Partner (Company A)
        ├── Institute (School 1)
        │     ├── Teachers
        │     └── Students
        ├── Institute (School 2)
        └── Sub-Partner (Company B)
              └── Institute (School 3)
```

Each partner can have multiple institutes, and partners can have sub-partners forming a tree structure.

---

## Creating a Partner

{% hint style="info" %}
Requires `partner_operation` permission if you are a team member.
{% endhint %}

1. Navigate to **Partners** from the sidebar
2. Click **Add Partner**
3. Fill in the required details:

| Field                | Required | Description                                       |
| -------------------- | -------- | ------------------------------------------------- |
| Name                 | Yes      | Contact person name                               |
| Email                | Yes      | Partner login email                                |
| Phone                | Yes      | Contact phone number                               |
| Company Name         | Yes      | Organization / brand name                          |
| Partner URL          | No       | Custom domain for white-label login                |
| Partner Logo         | No       | Brand logo (requires subscription with logo upload)|

4. Click **Create** to send an invitation

![Create Partner Form](../.gitbook/assets/create-partner-form.png)

{% hint style="warning" %}
The partner email must be unique across the platform. Duplicate emails are detected and an alert is shown.
{% endhint %}

---

## Viewing Partner Details

Click on any partner in the list to view their detail page:

### Overview Tab

- Partner profile information
- Company details and branding
- Assigned subscription plan
- Billing status and seat pool summary

### Institutes Tab

- List of all institutes under this partner
- Institute approval status
- Seat allocations per institute

### Courses Tab

- Courses assigned to this partner
- Course visibility and enrollment stats

### Billing Tab

- Current billing cycle status
- Invoice history
- Payment records

---

## Assigning Courses to Partners

1. Navigate to the partner's detail page
2. Go to the **Courses** tab
3. Click **Assign Courses**
4. Select one or more courses from the available list
5. Confirm the assignment

Assigned courses become available to all institutes under that partner.

---

## Managing Sub-Partners

Partners can create sub-partners to extend their network:

1. Go to the partner's detail page
2. Navigate to the **Sub-Partners** section
3. Click **Add Sub-Partner**
4. Fill in the sub-partner details

Sub-partners inherit course assignments from their parent partner and can have their own institutes.

{% hint style="info" %}
Use `GET /partners/allsubpartners/:parentId` to view the full sub-partner tree.
{% endhint %}

---

## Subscription Plans

Each partner can be assigned a subscription plan that controls their features:

| Feature              | Description                                     |
| -------------------- | ----------------------------------------------- |
| `allow_logo_upload`  | Partner can upload a custom logo                |
| `allow_custom_domain`| Partner can set a custom domain URL             |
| Seat limits          | Maximum number of seats the partner can purchase|

### Assigning a Subscription Plan

1. Go to the partner's detail page
2. Click **Assign Subscription Plan**
3. Select a plan from the available options
4. Optionally set:
   - Partner URL (custom domain)
   - Partner Company Name
   - Partner Logo
5. Confirm the assignment

---

## Seat Management

Partners purchase seats in bulk which are then allocated to their institutes:

### Seat Pool

| Metric           | Description                          |
| ---------------- | ------------------------------------ |
| Total Seats      | Total seats purchased by the partner |
| Allocated Seats  | Seats distributed to institutes      |
| Free Seats       | Unallocated seats available          |

### Purchasing Seats

1. Navigate to the partner's billing section
2. Click **Purchase Seats**
3. Enter the number of seats
4. Confirm the purchase — an invoice is generated

### Allocating Seats to Institutes

1. Go to the partner's **Institutes** tab
2. Select an institute
3. Click **Allocate Seats**
4. Enter the number of seats to allocate
5. Confirm — seats are moved from the partner's free pool

---

## Partner Statuses

| Status     | Description                                                 |
| ---------- | ----------------------------------------------------------- |
| Active     | Partner is operational with valid billing                   |
| Invoiced   | Invoice generated, awaiting payment                         |
| Suspended  | Payment overdue — all write operations blocked              |
| Deleted    | Soft-deleted — can be restored via `POST /partners/:id/restore` |

{% hint style="danger" %}
When a partner is **Suspended**, all write operations are blocked for the partner, their institutes, teachers, and students. Only payment resolution lifts the suspension.
{% endhint %}

---

## Deleting and Restoring Partners

### Deleting a Partner

1. Navigate to the partner's detail page
2. Click **Delete Partner**
3. Confirm the deletion

This performs a **soft delete** — the partner's data is preserved but access is revoked.

### Restoring a Partner

1. Use the admin interface or API to restore: `POST /partners/:id/restore`
2. The partner regains access with their previous configuration

---

## Next Steps

- [Managing Teams](managing-teams.md) — Delegate partner management tasks
- [Coupons and Pricing](coupons-and-pricing.md) — Set up discounts for partners
