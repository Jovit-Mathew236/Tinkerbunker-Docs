# Creating Courses

The Admin Creator role is responsible for building course content from scratch. This guide walks through the complete course creation flow: creating a course, adding chapters, adding pages, and embedding tests.

---

## Course Creation Flow

```
Create Course → Add Chapters → Add Pages → Add Embedded Tests → Submit for Review
```

{% hint style="info" %}
All newly created courses start in **Draft** status. They must be submitted for review before they can be approved and published.
{% endhint %}

---

## Step 1: Create a New Course

1. Navigate to **Courses** from the sidebar
2. Click **Create Course**
3. Fill in the course details:

### Basic Information

| Field            | Required | Description                                           |
| ---------------- | -------- | ----------------------------------------------------- |
| Title            | Yes      | Course name (displayed to students)                   |
| Description      | Yes      | Course overview and learning objectives                |
| Category         | Yes      | Primary category (managed by Super Admin)              |
| Sub-Category     | No       | Further classification within the category             |
| Grade Level From | Yes      | Minimum grade level                                    |
| Grade Level To   | Yes      | Maximum grade level                                    |
| Tags             | No       | Keywords for search and discovery                      |
| Objectives       | No       | Learning objectives listed as bullet points            |

### Media Assets

| Field      | Required | Description                        |
| ---------- | -------- | ---------------------------------- |
| Banner     | No       | Wide banner image for course page  |
| Thumbnail  | No       | Square thumbnail for course cards  |
| Video      | No       | Introductory video                  |

### Course Settings

| Field       | Required | Description                                      |
| ----------- | -------- | ------------------------------------------------ |
| Is Public   | No       | Whether the course is visible to public users    |
| Is Paid     | No       | Whether enrollment requires payment              |
| Price       | No       | Price in paisa (only if `is_paid` is true)       |
| Points      | No       | Reward points earned upon completion              |

4. Click **Create** to save the course in **Draft** status

![Create Course Form](../../.gitbook/assets/create-course-form.png)

---

## Step 2: Add Chapters

Chapters are the primary organizational units within a course. Each chapter contains pages and optional embedded tests.

1. Open the course you just created
2. Click **Add Chapter**
3. Enter the chapter title and description
4. Set the chapter order (drag-and-drop supported)
5. Click **Save**

### Chapter Structure

```
Course
  ├── Chapter 1
  │     ├── Page 1 (content)
  │     ├── Page 2 (content)
  │     └── Test 1 (inline_test)
  ├── Chapter 2
  │     ├── Page 1 (content)
  │     └── Page 2 (content)
  └── Pre-Test (pre_test)
  └── Post-Test (post_test)
```

{% hint style="info" %}
Chapters have an `order` field that determines their sequence in the course. You can reorder chapters by dragging them.
{% endhint %}

---

## Step 3: Add Pages

Pages are the content units within a chapter. Each page can contain rich text, images, videos, and other media.

1. Open a chapter
2. Click **Add Page**
3. Use the content editor to create your page:
   - Rich text formatting
   - Image embedding
   - Video embedding
   - Code blocks
   - Mathematical equations
4. Set the page order within the chapter
5. Click **Save**

### Content Types

Each chapter content item has a `type` field:

| Type   | Description                              |
| ------ | ---------------------------------------- |
| `page` | Regular content page                     |
| `test` | Embedded test (see Step 4)               |

---

## Step 4: Add Embedded Tests

Tests can be embedded directly within chapters to assess student understanding.

### Test Types

{% tabs %}
{% tab title="Pre-Test" %}
**Pre-tests** assess student knowledge before they begin the course.

- Appears at the beginning of the course
- Results help tailor the learning experience
- Configured at the course level (not per chapter)

1. Go to course settings
2. Enable **Pre-Test**
3. Add questions to the pre-test
{% endtab %}

{% tab title="Post-Test" %}
**Post-tests** evaluate student learning after completing the course.

- Appears at the end of the course
- Results contribute to completion percentage and certificate generation
- Configured at the course level

1. Go to course settings
2. Enable **Post-Test**
3. Add questions to the post-test
{% endtab %}

{% tab title="Inline Test" %}
**Inline tests** are embedded within chapters for periodic assessment.

- Appears between pages within a chapter
- Has an `order` field to position it relative to pages
- Can have attempt limits

1. Open a chapter
2. Click **Add Test** (or add content with type `test`)
3. Configure the test settings
4. Add questions
{% endtab %}
{% endtabs %}

### Question Formats

| Format       | Description                                        |
| ------------ | -------------------------------------------------- |
| `mcq`        | Multiple choice questions with single/multi select |
| `descriptive`| Free-form text answer                              |
| `code`       | Code-based question with editor                    |

### Test Attempt Configuration

| Setting              | Description                                    |
| -------------------- | ---------------------------------------------- |
| Default Max Attempts | Maximum number of times a student can attempt  |
| Is Locked            | Whether the test locks after max attempts      |

---

## Step 5: Sync Content

After adding all chapters, pages, and tests, sync the course content:

1. Click **Sync Content** on the course page
2. The system validates all content structure
3. Chapter order, page order, and test placement are finalized

{% hint style="warning" %}
Always sync content before submitting for review. Unsynced changes may not be visible to the publisher during review.
{% endhint %}

---

## Step 6: Submit for Review

Once your course content is complete:

1. Open the course
2. Click **Change Status**
3. Select **Submit for Review** (changes status from `draft` to `pending_review`)
4. The course moves from the **Drafts** tab to the **Pending Review** tab

![Submit for Review](../../.gitbook/assets/submit-for-review.png)

{% hint style="info" %}
After submission, the course appears in the Admin Publisher's review queue. You can still view the course but cannot edit it until the review is complete.
{% endhint %}

---

## Course Import

Admin Creators can also import existing courses:

1. Navigate to **Courses**
2. Click **Import Course**
3. Upload the course data file
4. Review the imported content
5. The course is created in **Draft** status

---

## Course Versioning

Courses support versioning through a parent-child relationship:

- `parent_course_id` links a new version to the original course
- `version` field tracks the version number
- When editing an approved course, a `REVISION` copy is created

This ensures the live version remains unchanged while edits are in progress.

---

## Dashboard Tabs (Admin Creator)

| Tab             | Shows                                              |
| --------------- | -------------------------------------------------- |
| **Live**        | Courses with `approved` status                     |
| **Rejected**    | Courses with `changes_requested` status            |
| **Drafts**      | Courses with `draft` status                        |
| **Pending Review** | Courses with `pending_review` or `revision` status |
| **Categories**  | Browse courses by category                         |

---

## Next Steps

- [Managing Content](managing-content.md) — Edit and update existing courses
- [Managing Teams](managing-teams.md) — Add team members to help with course creation
