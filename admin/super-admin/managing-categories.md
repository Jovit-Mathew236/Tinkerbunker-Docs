# Managing Categories

Course categories are managed exclusively by the Super Admin. Categories provide the organizational structure for courses and help users discover relevant content.

---

## Overview

Categories form a two-level hierarchy:

```
Category (e.g., "Science")
  ├── Sub-Category (e.g., "Physics")
  ├── Sub-Category (e.g., "Chemistry")
  └── Sub-Category (e.g., "Biology")
```

{% hint style="info" %}
Only **Super Admins** can manage categories. This page and all category endpoints are protected by the `SuperAdminOnlyGuard`.
{% endhint %}

---

## Accessing Category Management

1. Navigate to **Categories** from the sidebar
2. The category management page displays all existing categories

<figure><img src="../../.gitbook/assets/category-management.png" alt="Category Management Page"><figcaption></figcaption></figure>

---

## Creating a Category

1. Click **Add Category**
2. Fill in the details:

| Field       | Required | Description                                       |
| ----------- | -------- | ------------------------------------------------- |
| Name        | Yes      | Unique category name                              |
| Description | No       | Brief description of what the category covers     |

3. Click **Create**

{% hint style="warning" %}
Category names must be **unique** across the platform. Attempting to create a duplicate name will result in an error.
{% endhint %}

---

## Creating Sub-Categories

1. Click on a category to expand it
2. Click **Add Sub-Category**
3. Fill in:

| Field       | Required | Description                                    |
| ----------- | -------- | ---------------------------------------------- |
| Name        | Yes      | Sub-category name (unique within the category) |
| Description | No       | Brief description                              |

4. Click **Create**

---

## Editing a Category

1. Click the **Edit** icon on the category row
2. Update the name or description
3. Click **Save**

{% hint style="info" %}
Renaming a category automatically updates all courses associated with it.
{% endhint %}

---

## Deleting a Category

1. Click the **Delete** icon on the category row
2. Confirm the deletion

{% hint style="danger" %}
**Before deleting a category:**
- Ensure no courses are assigned to this category
- If courses exist under the category, reassign them first
- Deleting a category with sub-categories removes the sub-categories as well
{% endhint %}

---

## CRUD Operations Summary

| Operation | Endpoint                    | Description                |
| --------- | --------------------------- | -------------------------- |
| Create    | `POST /categories`          | Create a new category      |
| Read All  | `GET /categories`           | List all categories        |
| Read One  | `GET /categories/:id`       | Get a specific category    |
| Update    | `PATCH /categories/:id`     | Update category details    |
| Delete    | `DELETE /categories/:id`    | Delete a category          |

---

## Categories in Course Creation

When Admin Creators create or edit a course, they select from the categories you manage:

1. Creator opens the course form
2. Selects a **Category** from the dropdown
3. Selects a **Sub-Category** (optional, filtered by category)
4. The course is tagged with the selected category/sub-category

### Category Browsing

All admin roles can browse courses by category via the **Categories** tab in the courses section. This provides a filtered view of courses organized by your category structure.

---

## Best Practices

1. **Keep categories broad** — Use sub-categories for specific topics
2. **Use clear naming** — Category names should be self-explanatory
3. **Review periodically** — Remove unused categories and consolidate overlaps
4. **Plan before creating** — Establish a category taxonomy before creators start adding courses
5. **Limit depth** — Two levels (category + sub-category) is the supported depth

---

## Next Steps

- [Managing Courses](managing-courses.md) — Oversee all courses across the platform
