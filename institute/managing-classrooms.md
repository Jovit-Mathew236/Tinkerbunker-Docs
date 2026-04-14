---
description: How to create, edit, and manage classrooms within your institute.
---

# Managing Classrooms

Classrooms are the primary organizational unit inside an institute. Each classroom groups students and teachers together and can have one or more courses linked to it.

---

## Creating a Classroom

1. Navigate to **Dashboard → Classrooms**.
2. Click **Create Classroom**.
3. Fill in the required fields:

| Field              | Required | Description                                      |
| ------------------ | -------- | ------------------------------------------------ |
| **Classroom Name** | Yes      | A descriptive name (e.g., "Grade 10 — Section A") |
| **Grade**          | Yes      | The grade level this classroom belongs to.       |
| **Division**       | No       | Optional division or section identifier.         |
| **Description**    | No       | Short description visible to teachers/students.  |

4. Click **Save** to create the classroom.

<figure><img src="../.gitbook/assets/institute-create-classroom.png" alt="Create Classroom Form"><figcaption><p>Classroom creation form</p></figcaption></figure>

{% hint style="info" %}
A classroom must have at least one course linked before students can access any content.
{% endhint %}

---

## Editing a Classroom

1. Go to **Dashboard → Classrooms**.
2. Locate the classroom and click the **Edit** (pencil) icon.
3. Modify any of the editable fields.
4. Click **Save Changes**.

{% hint style="warning" %}
Renaming a classroom does not affect enrolled students or linked courses. All associations remain intact.
{% endhint %}

---

## Assigning Teachers

Teachers are assigned at the classroom level. A single teacher can be assigned to multiple classrooms.

1. Open the classroom detail view.
2. Navigate to the **Teachers** tab.
3. Click **Assign Teacher**.
4. Search for the teacher by name or email.
5. Select the teacher and confirm.

{% hint style="info" %}
Teachers must have an approved account within the institute before they can be assigned. See [Approving Users](approving-users.md) for the approval workflow.
{% endhint %}

---

## Assigning Students

Students can be added to a classroom individually or in bulk.

{% tabs %}
{% tab title="Individual Assignment" %}
1. Open the classroom detail view.
2. Navigate to the **Students** tab.
3. Click **Add Student**.
4. Search by name, email, or student ID.
5. Select the student and confirm.
{% endtab %}

{% tab title="Bulk Assignment" %}
1. Open the classroom detail view.
2. Navigate to the **Students** tab.
3. Click **Bulk Add**.
4. Upload a CSV file with student identifiers (email or student ID).
5. Review the preview and confirm.

The CSV format should be:

```
email
student1@example.com
student2@example.com
```
{% endtab %}
{% endtabs %}

---

## Linking Courses

Courses assigned to your institute can be linked to one or more classrooms. Linking a course makes its content available to all students enrolled in that classroom.

1. Open the classroom detail view.
2. Navigate to the **Courses** tab.
3. Click **Link Course**.
4. Select from the list of available institute courses.
5. Confirm the selection.

{% hint style="danger" %}
Unlinking a course from a classroom removes student access to that course content immediately. Student progress data is preserved but will not be visible until the course is re-linked.
{% endhint %}

---

## Deleting a Classroom

1. Go to **Dashboard → Classrooms**.
2. Click the **Delete** icon next to the classroom.
3. Confirm the deletion in the dialog.

{% hint style="danger" %}
Deleting a classroom is irreversible. All teacher and student associations for that classroom are removed. Student progress on linked courses is not deleted but will no longer be grouped under this classroom.
{% endhint %}

---

## Related

- [Managing Courses](managing-courses.md)
- [Approving Users](approving-users.md)
