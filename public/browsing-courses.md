# Browsing Courses

Public users can browse and discover courses on TinkerBunker without creating an account or logging in.

---

## Course Catalog

The public course catalog displays all courses marked as `is_public: true` and with `APPROVED` status.

![Public Course Catalog](../.gitbook/assets/public-course-catalog.png)

---

## Discovering Courses

### Browse the Catalog

1. Visit the TinkerBunker homepage
2. Navigate to **Courses**
3. Browse available courses displayed as cards

### Course Cards

Each course card displays:

| Element    | Description                          |
| ---------- | ------------------------------------ |
| Thumbnail  | Course thumbnail image               |
| Title      | Course name                          |
| Category   | Course category and sub-category     |
| Grade      | Target grade level range             |
| Price      | Free or price in INR                 |
| Tags       | Relevant keywords                    |

### Filtering and Search

| Filter        | Description                                 |
| ------------- | ------------------------------------------- |
| Search        | Search by course title or keywords          |
| Category      | Filter by course category                   |
| Sub-Category  | Further filter by sub-category              |
| Grade Level   | Filter by target grade range                |
| Price         | Free or Paid courses                        |

---

## Viewing Course Details

Click on any course card to view its full details:

### Course Overview

- **Description** — Full course description and objectives
- **Chapters** — List of chapters and their content outline
- **Prerequisites** — Required knowledge or prior courses
- **Learning Objectives** — What you will learn
- **Grade Level** — Target audience range

### Media

- **Banner Image** — Full-width course banner
- **Video** — Introductory video (if available)

### Enrollment Information

- **Free courses** — Show an **Enroll** button
- **Paid courses** — Show the price and a **Buy Now** button

---

## Course Visibility Rules

Not all courses appear in the public catalog:

| Setting              | Public Visibility                         |
| -------------------- | ----------------------------------------- |
| `is_public: true`    | Visible in the public catalog             |
| `is_public: false`   | Not visible — only accessible via direct assignment |
| Status: `APPROVED`   | Visible (if public)                       |
| Status: Others       | Not visible to public users               |

{% hint style="info" %}
Private courses are only accessible to students enrolled through their institute or partner. They do not appear in the public catalog.
{% endhint %}

---

## White-Labeled Course Browsing

If you access TinkerBunker through a partner's custom domain:

1. The login page shows the partner's branding (logo and company name)
2. Available courses may be filtered to only those assigned to that partner
3. The overall experience reflects the partner's white-label configuration

---

## Without an Account

Public users can:

- Browse the course catalog
- View course details and structure
- Verify certificates (see [Verify Certificate](verify-certificate.md))

Public users cannot:

- Enroll in courses (requires account creation)
- Track progress
- Take tests
- Earn certificates

{% hint style="info" %}
To enroll in a course, you need to create an account. See [Enrolling in Courses](enrolling.md) for details.
{% endhint %}

---

## Next Steps

- [Enrolling in Courses](enrolling.md) — Create an account and start learning
- [Verify Certificate](verify-certificate.md) — Verify a certificate's authenticity
