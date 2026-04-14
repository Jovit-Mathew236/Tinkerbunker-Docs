# Reviewing Courses

The Admin Publisher is responsible for reviewing courses submitted by Admin Creators. This guide covers the review workflow, approval and rejection processes, and providing feedback.

---

## Review Dashboard

When you log in as an Admin Publisher, your dashboard displays:

- **Pending Review Courses** — Courses awaiting your review
- **Live Courses** — Courses that have been approved and are live
- **Sales Table** — Overview of sales personnel

### Navigation

| Nav Item | Path       | Description                      |
| -------- | ---------- | -------------------------------- |
| Courses  | `/courses` | Review and manage courses        |
| Sales    | `/sales`   | Manage sales personnel           |

### Course Tabs

| Tab          | Shows                                        |
| ------------ | -------------------------------------------- |
| **Review**   | Courses with `pending_review` or `revision` status |
| **Approved** | Courses with `approved` status               |
| **Categories** | Browse courses by category                 |

---

## Review Workflow

```
Creator submits course (PENDING_REVIEW)
         │
         ▼
Publisher reviews course content
         │
    ┌────┴────┐
    ▼         ▼
 APPROVE   REJECT
    │         │
    ▼         ▼
 APPROVED  CHANGES_REQUESTED
 (Live)    (Back to Creator)
```

---

## Reviewing a Course

1. Navigate to **Courses** > **Review** tab
2. Click on a course to open the review view
3. Review the following:

### Content Review Checklist

| Area             | What to Check                                    |
| ---------------- | ------------------------------------------------ |
| Course Details   | Title, description, category, grade level        |
| Chapters         | Proper structure, logical ordering               |
| Pages            | Content quality, media assets, formatting        |
| Tests            | Question quality, correct answers, attempt config|
| Pre/Post Tests   | Aligned with learning objectives                 |
| Media            | Banner, thumbnail, video quality                 |
| Settings         | Visibility (public/private), pricing             |

<figure><img src="../../.gitbook/assets/course-review-view.png" alt="Course Review View"><figcaption></figcaption></figure>

---

## Approving a Course

1. Open the course in review
2. Click **Approve**
3. The **Approve Modal** appears
4. Confirm the approval

### What Happens on Approval

- Course status changes to `APPROVED`
- **Milestones are regenerated** for the course structure
- Course becomes visible based on its visibility settings:
  - Public courses appear in the course catalog
  - Private courses are only visible to assigned partners/institutes
- If this is a **revision**, the previous version is archived

{% hint style="info" %}
Approving a course triggers milestone regeneration. This ensures the course progress tracking is aligned with the current content structure.
{% endhint %}

---

## Rejecting a Course

1. Open the course in review
2. Click **Reject**
3. The **Reject Modal** appears
4. Provide detailed feedback explaining the reasons for rejection:

### Feedback Fields

| Field    | Required | Description                                      |
| -------- | -------- | ------------------------------------------------ |
| Feedback | Yes      | Detailed explanation of what needs to be changed |

5. Click **Submit Rejection**

### What Happens on Rejection

- Course status changes to `CHANGES_REQUESTED`
- The course moves back to the Creator's **Rejected** tab
- Creator can view the feedback and make corrections
- Creator can then resubmit for review

{% hint style="warning" %}
Provide specific, actionable feedback when rejecting a course. Vague feedback leads to repeated rejection cycles.
{% endhint %}

---

## Reviewing Revisions

When a Creator edits an approved course, a **Revision** is created:

1. Revisions appear in the **Review** tab alongside new submissions
2. The review process is identical to new courses
3. On approval, the revision replaces the live version
4. The previous version is archived with `MERGED` status

---

## Status Transitions (Publisher Permissions)

As an Admin Publisher, you can make the following status transitions:

| From               | To                    | Action                    |
| ------------------ | --------------------- | ------------------------- |
| `PENDING_REVIEW`   | `APPROVED`            | Approve the course        |
| `PENDING_REVIEW`   | `CHANGES_REQUESTED`   | Reject with feedback      |
| `APPROVED`         | `CHANGES_REQUESTED`   | Revoke approval           |
| `REVISION`         | `APPROVED`            | Approve the revision      |
| `REVISION`         | `CHANGES_REQUESTED`   | Reject the revision       |

---

## Course Assignment

After approving a course, you can assign it to partners:

1. Open the approved course
2. Click **Assign Course**
3. Select target partners from the list
4. Confirm the assignment

Assigned courses become available to all institutes under the selected partners.

{% hint style="info" %}
Course assignment at the partner level cascades to all institutes under that partner.
{% endhint %}

---

## Next Steps

- [Publishing Courses](publishing-courses.md) — Make approved courses live
- [Managing Sales](managing-sales.md) — Set up your sales team
