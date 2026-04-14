# Managing Content

This guide covers editing existing courses, updating content, and managing course versions as an Admin Creator.

---

## Editing Existing Courses

### Draft Courses

Courses in **Draft** status can be freely edited:

1. Navigate to **Courses** > **Drafts** tab
2. Click on the course to open it
3. Edit any field — title, description, chapters, pages, tests
4. Click **Save** to persist changes

### Approved Courses (Creating a Revision)

Editing an approved (live) course creates a **Revision**:

1. Navigate to **Courses** > **Live** tab
2. Click on the course
3. Click **Edit Course**
4. The system creates a `REVISION` copy linked to the original via `parent_course_id`
5. Make your changes on the revision
6. Submit the revision for review

{% hint style="warning" %}
The live version of the course remains unchanged and accessible to students while the revision is under review. Once approved, the revision replaces the live version.
{% endhint %}

### Rejected Courses

Courses with `changes_requested` status can be edited to address reviewer feedback:

1. Navigate to **Courses** > **Rejected** tab
2. Click on the course to view the rejection feedback
3. Address the feedback by editing the content
4. Change status back to **Draft** or directly to **Pending Review**

---

## Updating Chapters

### Reordering Chapters

1. Open the course editor
2. Drag chapters to rearrange their order
3. The `order` field updates automatically
4. Click **Sync Content** to finalize the order

### Editing Chapter Content

1. Click on a chapter to expand it
2. Edit the chapter title or description
3. Add, remove, or reorder pages and tests within the chapter
4. Save changes

### Deleting Chapters

1. Click the delete icon on the chapter
2. Confirm the deletion

{% hint style="danger" %}
Deleting a chapter removes all pages and tests within it. This action cannot be undone.
{% endhint %}

---

## Updating Pages

### Editing Page Content

1. Open a chapter
2. Click on the page to edit
3. Use the rich text editor to update content
4. Save changes

### Page Operations

| Action    | Description                                     |
| --------- | ----------------------------------------------- |
| Edit      | Modify page content and settings                |
| Reorder   | Change position within the chapter              |
| Delete    | Remove the page from the chapter                |
| Duplicate | Create a copy of the page                       |

---

## Updating Tests

### Editing Test Questions

1. Open the chapter containing the test
2. Click on the test to edit
3. Modify questions, options, or correct answers
4. Update attempt configuration if needed
5. Save changes

### Test Configuration Updates

| Setting              | Editable | Notes                                      |
| -------------------- | -------- | ------------------------------------------ |
| Question text        | Yes      | Can be updated at any time in draft         |
| Answer options       | Yes      | MCQ options can be added/removed/modified   |
| Correct answers      | Yes      | Mark new correct answers                    |
| Max attempts         | Yes      | Change the attempt limit                    |
| Lock status          | Yes      | Toggle whether test locks after max attempts|
| Test type            | No       | Cannot change between pre/post/inline       |

---

## Content Syncing

After making changes to course structure (adding/removing/reordering chapters, pages, or tests), always sync:

1. Click **Sync Content** on the course page
2. The system validates:
   - Chapter ordering is sequential
   - Page ordering within chapters is correct
   - Test placement is valid
   - All required content is present
3. Sync completes and the course is ready for review

{% hint style="info" %}
Syncing is required before submitting for review. The system ensures structural integrity of the course hierarchy.
{% endhint %}

---

## Content Versioning

TinkerBunker tracks course versions to maintain content history:

| Field              | Description                                         |
| ------------------ | --------------------------------------------------- |
| `version`          | Numeric version identifier                          |
| `parent_course_id` | Links to the original course (for revisions)        |
| `created_by_user_id` | Tracks who created the content                    |
| `creator_type`     | Role of the creator                                  |

### Version History

- Each approved course represents a stable version
- Revisions create new entries linked to the parent
- Upon approval, the revision merges into the main course
- Previous versions are preserved with `MERGED` or `ARCHIVED` status

---

## Course Status Transitions (Creator Permissions)

As an Admin Creator, you can make the following status transitions:

| From                  | To                | Action                 |
| --------------------- | ----------------- | ---------------------- |
| `DRAFT`               | `PENDING_REVIEW`  | Submit for review      |
| `CHANGES_REQUESTED`   | `DRAFT`           | Return to draft        |
| `CHANGES_REQUESTED`   | `PENDING_REVIEW`  | Resubmit for review    |
| `REVISION`            | `PENDING_REVIEW`  | Submit revision        |

{% hint style="info" %}
You cannot directly set a course to `APPROVED` — only Admin Publishers can approve courses.
{% endhint %}

---

## Deleting Courses

1. Navigate to the course you want to delete
2. Click **Delete Course**
3. Confirm the deletion

This performs a **soft delete**. The course is removed from your view but can be restored if needed.

{% hint style="warning" %}
You can only delete courses in **Draft** or **Changes Requested** status. Approved/live courses cannot be deleted directly.
{% endhint %}

---

## Next Steps

- [Creating Courses](creating-courses.md) — Start a new course from scratch
- [Managing Teams](managing-teams.md) — Collaborate with team members on content
