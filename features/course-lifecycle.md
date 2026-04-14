# Course Lifecycle

The course lifecycle in TinkerBunker follows a structured workflow that ensures content quality through a review process. Multiple roles interact at each stage.

---

## Lifecycle Overview

```
┌──────────┐     ┌────────────────┐     ┌──────────┐
│          │     │                │     │          │
│  DRAFT   ├────►│ PENDING REVIEW ├────►│ APPROVED │
│          │     │                │     │  (Live)  │
└──────────┘     └───────┬────────┘     └──────────┘
     ▲                   │
     │                   ▼
     │           ┌───────────────────┐
     └───────────┤ CHANGES REQUESTED │
                 │   (Rejected)      │
                 └───────────────────┘

                  ┌──────────┐
                  │ REVISION │──► PENDING REVIEW ──► APPROVED
                  └──────────┘                   └─► CHANGES REQUESTED

                  ┌──────────┐     ┌────────┐
                  │ ARCHIVED │     │ MERGED │
                  └──────────┘     └────────┘
```

---

## Status Definitions

| Status               | Description                                                   |
| -------------------- | ------------------------------------------------------------- |
| `DRAFT`              | Course is being created. Only visible to the Admin Creator.   |
| `PENDING_REVIEW`     | Course submitted for review. Visible to Creator and Publisher.|
| `APPROVED`           | Course is live and accessible based on visibility settings.   |
| `CHANGES_REQUESTED`  | Course rejected with feedback. Returned to Creator for edits. |
| `REVISION`           | An approved course being edited. Creates a copy for review.   |
| `ARCHIVED`           | Course has been retired. Not visible to end users.            |
| `MERGED`             | Previous version merged after revision approval. Internal use.|

---

## Stage-by-Stage Breakdown

### Stage 1: Draft

**Who:** Admin Creator

**Actions:**
1. Create a new course with title, description, category, and settings
2. Add chapters with ordered content
3. Add pages with rich text, images, and media
4. Add embedded tests (pre-test, post-test, inline tests)
5. Configure visibility (`is_public`, `is_paid`, `price_paisa`)
6. Sync content to finalize structure

**Next:** Submit for review (`DRAFT` → `PENDING_REVIEW`)

{% hint style="info" %}
Courses can remain in Draft indefinitely. There is no time limit for submission.
{% endhint %}

---

### Stage 2: Pending Review

**Who:** Admin Publisher (reviewer), Admin Creator (read-only)

**Actions:**
1. Publisher reviews course content, structure, and quality
2. Publisher checks chapters, pages, tests, and media
3. Publisher decides: **Approve** or **Reject**

**Possible transitions:**
- `PENDING_REVIEW` → `APPROVED` (Publisher approves)
- `PENDING_REVIEW` → `CHANGES_REQUESTED` (Publisher rejects with feedback)

{% hint style="warning" %}
While a course is in review, the Admin Creator can view it but cannot make edits.
{% endhint %}

---

### Stage 3a: Approved (Live)

**Who:** All roles (based on visibility and assignment)

**What happens on approval:**
1. Course status changes to `APPROVED`
2. Milestones are regenerated for progress tracking
3. Course becomes accessible:
   - **Public courses** appear in the catalog
   - **Private courses** are available to assigned partners/institutes
4. Students can enroll (free) or purchase (paid)

**Possible transitions:**
- `APPROVED` → `CHANGES_REQUESTED` (Publisher revokes approval)
- `APPROVED` → `REVISION` (Creator starts editing the live course)

---

### Stage 3b: Changes Requested (Rejected)

**Who:** Admin Creator

**What happens on rejection:**
1. Course status changes to `CHANGES_REQUESTED`
2. Feedback from the Publisher is attached to the course
3. Course appears in the Creator's **Rejected** tab
4. Creator reviews feedback and makes corrections

**Possible transitions:**
- `CHANGES_REQUESTED` → `DRAFT` (Creator returns to drafting)
- `CHANGES_REQUESTED` → `PENDING_REVIEW` (Creator resubmits directly)

---

### Stage 4: Revision

**Who:** Admin Creator (editing), Admin Publisher (reviewing)

When an Admin Creator edits an approved course:

1. A `REVISION` copy is created, linked via `parent_course_id`
2. The live version remains unchanged and accessible
3. Creator makes changes on the revision copy
4. Creator submits the revision for review
5. Publisher reviews and approves/rejects

**On revision approval:**
- The revision replaces the live version
- The previous version is archived with `MERGED` status
- Milestones are regenerated

---

### Stage 5: Archived / Merged

**Who:** Super Admin (archive), System (merge)

| Status    | Trigger                                      | Purpose                           |
| --------- | -------------------------------------------- | --------------------------------- |
| `ARCHIVED`| Super Admin archives a course                | Retire old courses                |
| `MERGED`  | Revision approved, previous version merged   | Track version history             |

---

## Role Interactions by Stage

| Stage             | Admin Creator           | Admin Publisher         | Super Admin    | Students/Public |
| ----------------- | ----------------------- | ----------------------- | -------------- | --------------- |
| Draft             | Create, Edit, Submit    | --                      | View           | --              |
| Pending Review    | View only               | Review, Approve, Reject | View, Override | --              |
| Approved (Live)   | View, Start Revision    | View, Revoke, Assign    | View, Manage   | Enroll, Learn   |
| Changes Requested | Edit, Resubmit          | --                      | View, Override | --              |
| Revision          | Edit, Submit            | Review, Approve, Reject | View, Override | --              |
| Archived          | --                      | --                      | View, Restore  | --              |

---

## Status Transition Permissions

### Admin Creator Can:
| From                  | To                |
| --------------------- | ----------------- |
| `DRAFT`               | `PENDING_REVIEW`  |
| `REVISION`            | `PENDING_REVIEW`  |
| `CHANGES_REQUESTED`   | `DRAFT`           |
| `CHANGES_REQUESTED`   | `PENDING_REVIEW`  |

### Admin Publisher Can:
| From                  | To                    |
| --------------------- | --------------------- |
| `PENDING_REVIEW`      | `APPROVED`            |
| `PENDING_REVIEW`      | `CHANGES_REQUESTED`   |
| `APPROVED`            | `CHANGES_REQUESTED`   |
| `REVISION`            | `APPROVED`            |
| `REVISION`            | `CHANGES_REQUESTED`   |

### Super Admin Can:
| From      | To        |
| --------- | --------- |
| Any       | Any       |

{% hint style="info" %}
Status transitions are enforced by the `CourseStatusGuard` on the backend. Unauthorized transitions result in a 403 error.
{% endhint %}

---

## Next Steps

- [Creating Courses](../admin/creator/creating-courses.md) — Start building a course
- [Reviewing Courses](../admin/publisher/reviewing-courses.md) — Learn the review process
- [Managing Courses](../admin/super-admin/managing-courses.md) — Super Admin oversight
