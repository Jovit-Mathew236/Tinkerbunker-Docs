# Publishing Courses

After a course is approved, it becomes available based on its visibility settings. This guide covers the publishing process and course visibility configuration.

---

## Course Visibility Settings

Courses have several visibility and access options:

| Setting       | Values           | Description                                         |
| ------------- | ---------------- | --------------------------------------------------- |
| `is_public`   | `true` / `false` | Whether the course appears in the public catalog    |
| `is_paid`     | `true` / `false` | Whether enrollment requires payment                 |
| `price_paisa` | Number           | Price in paisa (only when `is_paid` is true)        |

### Visibility Matrix

| is_public | is_paid | Behavior                                              |
| --------- | ------- | ----------------------------------------------------- |
| `true`    | `false` | Free public course — anyone can enroll                |
| `true`    | `true`  | Paid public course — requires Razorpay payment        |
| `false`   | `false` | Private free course — only assigned partners/institutes |
| `false`   | `true`  | Private paid course — assigned users must pay          |

---

## Publishing Workflow

### From Approval to Live

```
PENDING_REVIEW → APPROVED (by Publisher) → Live and accessible
```

Once a course is approved:

1. The course status changes to `APPROVED`
2. Course milestones are regenerated
3. The course becomes visible based on its settings:
   - **Public courses** appear in the course catalog immediately
   - **Private courses** need to be assigned to partners/institutes

### Assigning Courses

For private courses (or to explicitly push courses to partners):

1. Open the approved course
2. Click **Assign Course**
3. Select one or more partners
4. The course becomes available to all institutes under those partners

{% hint style="info" %}
Course assignment works at the partner level. All institutes under a partner automatically get access to assigned courses.
{% endhint %}

---

## Managing Live Courses

### Viewing Approved Courses

1. Navigate to **Courses** > **Approved** tab
2. Browse all live courses
3. Click on any course to view details

### Revoking Approval

If a live course needs to be taken down:

1. Open the course
2. Click **Change Status**
3. Set status to `CHANGES_REQUESTED`
4. Provide feedback on why the course needs changes
5. The course is removed from the live catalog and returned to the Creator

{% hint style="warning" %}
Revoking approval immediately removes the course from all catalogs. Students currently enrolled may lose access to the course content.
{% endhint %}

---

## Enrollment Management

### Free Course Enrollment

Students can enroll in free public courses directly:

1. Student browses the course catalog
2. Clicks **Enroll**
3. Enrollment is created immediately
4. Student gains access to course content

### Paid Course Enrollment

For paid courses, the enrollment flow includes payment:

1. Student views the course and clicks **Enroll**
2. Razorpay checkout modal opens
3. Student completes payment
4. Payment is verified via Razorpay signature
5. Enrollment is created upon successful payment
6. `CourseEnrollment` record includes `razorpay_order_id` and `razorpay_payment_id`

---

## Course Status Overview

| Status              | Visibility            | Who Can See                        |
| ------------------- | --------------------- | ---------------------------------- |
| `DRAFT`             | Not visible           | Admin Creator only                 |
| `PENDING_REVIEW`    | Not visible           | Admin Creator + Admin Publisher    |
| `REVISION`          | Not visible           | Admin Creator + Admin Publisher    |
| `APPROVED`          | Live                  | All roles based on assignment      |
| `CHANGES_REQUESTED` | Not visible           | Admin Creator only                 |
| `ARCHIVED`          | Not visible           | Super Admin only                   |
| `MERGED`            | Not visible           | Internal use only                  |

---

## Post-Publishing Considerations

### Milestone Tracking

Upon approval, the system regenerates milestones for the course:

- Each chapter and test becomes a milestone
- Student progress is tracked against these milestones
- 100% milestone completion triggers certificate eligibility

### Course Analytics

After publishing, monitor course performance:

- Enrollment counts
- Completion rates
- Test scores
- Student feedback

---

## Next Steps

- [Reviewing Courses](reviewing-courses.md) — Continue reviewing submissions
- [Managing Sales](managing-sales.md) — Assign sales personnel to manage distribution
