---
description: Adding and managing institutes (schools) under your partner account, including grade and division management and remote devices.
---

# Managing Schools

Schools (institutes) are the organizations that operate under your partner account. As a partner, you can add new schools, manage their configurations, and oversee their operations.

---

## Viewing Your Schools

1. Navigate to **Dashboard → Schools**.
2. The school list displays all institutes under your partner account.

| Column            | Description                                           |
| ----------------- | ----------------------------------------------------- |
| **School Name**   | Name of the institute.                                |
| **Location**      | City or address of the institute.                     |
| **Students**      | Total enrolled students.                              |
| **Teachers**      | Total assigned teachers.                              |
| **Seats Used**    | Active seats out of allocated.                        |
| **Status**        | Active or Suspended.                                  |

<figure><img src="../.gitbook/assets/partner-school-list.png" alt="Partner School List"><figcaption><p>List of institutes managed under the partner account</p></figcaption></figure>

---

## Adding a New School

1. Go to **Dashboard → Schools**.
2. Click **Add School**.
3. Fill in the school details:

| Field              | Required | Description                                       |
| ------------------ | -------- | ------------------------------------------------- |
| **School Name**    | Yes      | Official name of the institute.                   |
| **Location**       | Yes      | City or full address.                             |
| **Contact Email**  | Yes      | Primary contact email for the institute.          |
| **Contact Phone**  | No       | Primary contact phone number.                     |
| **Admin Name**     | Yes      | Name of the institute admin who will manage it.   |
| **Admin Email**    | Yes      | Email for the institute admin account.            |

4. Click **Create School**.

{% hint style="info" %}
An invitation is automatically sent to the admin email. The institute admin must accept the invitation and set up their account before they can manage the school.
{% endhint %}

---

## Grade Management

Grades define the academic levels offered by a school. Managing grades ensures that courses are correctly mapped to classrooms.

### Adding Grades

1. Open the school detail view.
2. Navigate to the **Grades** tab.
3. Click **Add Grade**.
4. Enter the grade level (e.g., "Grade 5", "Class 10", "Year 8").
5. Click **Save**.

### Editing or Removing Grades

- Click **Edit** next to a grade to rename it.
- Click **Remove** to delete a grade.

{% hint style="warning" %}
Removing a grade that has active classrooms assigned to it will require you to reassign those classrooms to a different grade or delete them first.
{% endhint %}

---

## Division Management

Divisions (sections) are subdivisions within a grade. They help organize students into smaller groups.

### Adding Divisions

1. Open the school detail view.
2. Navigate to the **Grades** tab and select a grade.
3. Click **Add Division**.
4. Enter the division name (e.g., "Section A", "Division 1").
5. Click **Save**.

### Managing Divisions

| Action      | Description                                          |
| ----------- | ---------------------------------------------------- |
| **Rename**  | Click Edit to change the division name.              |
| **Remove**  | Click Remove to delete. Existing classrooms may need reassignment. |

{% hint style="info" %}
Grades and divisions provide structure for the institute admin when creating classrooms. They are organizational aids and do not restrict course access directly.
{% endhint %}

---

## Remote Devices

Partners can register and manage remote receiver devices for schools. These devices are used during live quiz sessions.

### Registering Devices for a School

1. Open the school detail view.
2. Navigate to the **Remote Devices** tab.
3. Click **Add Device**.
4. Enter the device details:

| Field           | Required | Description                                   |
| --------------- | -------- | --------------------------------------------- |
| **Device Name** | Yes      | Friendly label for the device.                |
| **Device ID**   | Yes      | Hardware identifier.                          |

5. Click **Register**.

{% hint style="info" %}
Devices registered at the partner level are available to the institute admin for classroom assignment. See the [Institute Remote Devices](../institute/remote-devices.md) guide for classroom-level setup.
{% endhint %}

### Viewing Device Status

The remote devices tab shows the status of all devices:

- **Online** — device is connected and communicating.
- **Offline** — device is not reachable.
- **Error** — device encountered an issue.

---

## Editing School Details

1. Go to **Dashboard → Schools**.
2. Click **Edit** next to the school.
3. Update the desired fields.
4. Click **Save Changes**.

---

## Suspending or Reactivating a School

{% tabs %}
{% tab title="Suspend" %}
1. Open the school detail view.
2. Click **Suspend School**.
3. Confirm the action.

Suspended schools retain their data but all users lose access until reactivated.
{% endtab %}

{% tab title="Reactivate" %}
1. Open the school detail view (filter by suspended schools).
2. Click **Reactivate School**.
3. Confirm the action.

All users regain their previous access levels.
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
Suspending a school immediately locks out all institute admins, teachers, and students. Use this as a last resort, such as for non-payment or compliance issues.
{% endhint %}

---

## Related

- [Dashboard](dashboard.md)
- [Seats and Licensing](seats-and-licensing.md)
- [Billing and Payments](billing-and-payments.md)
