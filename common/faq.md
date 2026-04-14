# Frequently Asked Questions

Common questions and answers about TinkerBunker, organized by topic.

---

## General

### 1. What is TinkerBunker?

TinkerBunker is a comprehensive learning management platform that enables organizations to create, distribute, and manage educational courses. It supports multiple roles from content creators to students, with features including course management, testing, certification, and partner billing.

### 2. What roles are available on the platform?

TinkerBunker supports 11 roles: Public, Student, Teacher, Guardian, Institute, Partner, Sales, Admin Creator, Admin Publisher, Super Admin, and Team Member. Each role has specific capabilities and access levels. See the [Role Access Matrix](../features/role-access-matrix.md) for details.

### 3. Can a user have multiple roles?

Yes. A single user can hold multiple roles simultaneously. Users can switch between their active roles using the **Role Switcher** in the profile dropdown menu. Each role provides a different view and set of capabilities.

---

## Courses

### 4. How do I create a course?

Courses are created by **Admin Creators**. Navigate to **Courses**, click **Create Course**, add your content (chapters, pages, tests), and submit for review. See [Creating Courses](../admin/creator/creating-courses.md) for the full guide.

### 5. How long does course review take?

Review times depend on the Admin Publisher's availability. There is no system-enforced time limit. Courses remain in **Pending Review** status until a Publisher takes action.

### 6. What happens when my course is rejected?

When a course is rejected, it moves to `CHANGES_REQUESTED` status with feedback from the Publisher. You can view the feedback, make corrections, and resubmit for review. See [Managing Content](../admin/creator/managing-content.md).

### 7. Can I edit a live course?

Yes, but editing a live course creates a **Revision** copy. The live version remains unchanged while you edit the revision. Once the revision is approved, it replaces the live version.

### 8. What course visibility options are available?

Courses can be:
- **Public + Free** — Anyone can enroll
- **Public + Paid** — Requires Razorpay payment
- **Private + Free** — Only assigned partners/institutes
- **Private + Paid** — Assigned users must pay

---

## Tests and Assessments

### 9. What types of tests does TinkerBunker support?

TinkerBunker supports: Pre-Tests, Post-Tests, Inline Tests (embedded in courses), Teacher Tests (standalone), Practice Tests, Assigned Tests with evaluation, Remote Quizzes (physical remotes), and Web Quizzes. See [Test System](../features/test-system.md).

### 10. How does the Remote Quiz work?

Remote Quiz uses physical USB receivers and remote clickers for live classroom quizzes. The teacher connects a USB receiver, maps students to remotes, and runs a real-time quiz. See [Remote Quiz](../features/remote-quiz.md).

### 11. Can tests be re-attempted?

Yes, based on the test configuration. Each test has `default_max_attempts` and `is_locked` settings. When `is_locked` is true, the test is locked after reaching maximum attempts.

---

## Certificates

### 12. How do I get a certificate?

Certificates are automatically generated when you complete a course with 100% progress (all milestones complete). Navigate to your certificates section to download the PDF.

### 13. How do I verify a certificate?

Visit `https://your-domain.com/verify-certificate/{uuid}` with the certificate's UUID. No login is required. The system cryptographically verifies the certificate's authenticity. See [Verify Certificate](../public/verify-certificate.md).

---

## Billing and Payments

### 14. How does billing work for partners?

Partners operate on a seat-based billing model. They purchase seats at the platform rate, which are allocated to their institutes. Invoices are generated per billing cycle and paid through Razorpay. See [Billing](../features/billing.md).

### 15. What payment methods are supported?

TinkerBunker integrates with **Razorpay**, supporting: UPI, Credit/Debit Cards, Net Banking, and Digital Wallets.

### 16. What happens if a partner doesn't pay their invoice?

Unpaid invoices result in a **Suspended** billing status. The `SuspendedPartnerGuard` blocks all write operations for the partner and their entire hierarchy (institutes, teachers, students) until payment is resolved.

---

## Approval and Access

### 17. How does the institute approval process work?

When you sign up and request to join an institute, your request enters a **Pending** state. The institute admin reviews and approves or rejects your request. While pending, you can only access the dashboard. See [Approval System](../features/approval-system.md).

### 18. How many times can I reapply if rejected?

You can reapply up to **5 times**. After 5 rejected attempts, you can no longer reapply and should contact support.

### 19. Can I switch to a different institute?

Yes. If your request is rejected, you can choose to **Change Institute** and apply to a different one.

---

## Teams

### 20. What are team members?

Team members are users who operate under a primary account (Partner, Institute, Sales, or Admin Creator) with delegated permissions. They log in with their own credentials but have restricted access based on assigned permissions.

### 21. What permissions can team members have?

Permissions depend on the team type:
- **Partner teams:** `school_operation`, `subpartner_operation`, `seat_operation`
- **Institute teams:** `classroom_operation`
- **Sales teams:** `partner_operation`, `coupon_operation`
- **Creator teams:** `course_operation`

---

## White Labeling

### 22. How do I set up white labeling for my partner account?

White labeling requires a subscription plan with `allow_logo_upload` and/or `allow_custom_domain`. Contact your Sales agent to assign the appropriate plan. Once enabled, you can upload your logo and set a custom domain. See [White Labeling](../features/white-labeling.md).

---

## Next Steps

- [Troubleshooting](troubleshooting.md) — Common issues and solutions
- [Glossary](glossary.md) — Platform terminology reference
