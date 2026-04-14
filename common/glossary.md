# Glossary

A reference of key terms and concepts used throughout the TinkerBunker platform.

---

## A

### Admin Creator
A role responsible for creating and managing course content. Admin Creators build courses with chapters, pages, and tests, then submit them for review.

### Admin Publisher
A role responsible for reviewing and approving courses submitted by Admin Creators. Admin Publishers also manage the sales team.

### Approval Status
The state of a user's request to join an institute. Values: `PENDING`, `APPROVED`, `REJECTED`, `CANCELLED`.

### Assigned Test
A teacher-created test that is formally assigned to a classroom with a due date and evaluation workflow.

---

## B

### Billing Cycle
A recurring period during which a partner is billed for their seat usage. Statuses: `ACTIVE`, `COMPLETED`, `INVOICED`, `SUSPENDED`.

### Billing Alert
A visual notification (banner) displayed when a partner has outstanding billing actions. Types: `INVOICED` (yellow), `SUSPENDED` (red), `ACTIVE` (dismissed).

---

## C

### Category
A top-level classification for courses (e.g., "Science", "Mathematics"). Managed exclusively by Super Admins.

### Certificate
A digitally signed document issued upon course completion. Contains a UUID for public verification, SHA-256 hash, and HMAC-SHA256 signature.

### Certificate UUID
A universally unique identifier assigned to each certificate, used for public verification without authentication.

### Chapter
An organizational unit within a course. Chapters contain pages and optional embedded tests, with an `order` field for sequencing.

### Classroom
A virtual class within an institute, grouping students and teachers for course delivery.

### Content Sync
The process of finalizing course structure (chapter order, page order, test placement) before submission for review.

### Controls
A JSONB field on team member entities that defines their delegated permissions (e.g., `{ seat_operation: true }`).

### Course
The primary educational content unit. Contains chapters, pages, and tests. Has a lifecycle from Draft to Approved.

### Course Enrollment
A record linking a user to a course, created upon free enrollment or successful payment. May include Razorpay payment references.

### Course Status
The current state of a course in its lifecycle. Values: `DRAFT`, `PENDING_REVIEW`, `APPROVED`, `CHANGES_REQUESTED`, `REVISION`, `ARCHIVED`, `MERGED`.

---

## D

### Dashboard
The role-specific landing page shown after login. Content varies by active role.

### Digital Signature
An HMAC-SHA256 signature applied to certificates to ensure authenticity and detect tampering.

### Draft
The initial status of a newly created course. Only visible to the Admin Creator.

---

## E

### Enrollment Status
Tracks whether a student is actively enrolled, has completed, or has been removed from a course.

---

## F

### Favorites
A feature allowing students and teachers to bookmark courses for quick access.

### Free Seats
Seats in a partner's pool that have not been allocated to any institute.

---

## G

### Global Pricing
The platform-wide price per seat and GST percentage, managed by the Super Admin.

### GST
Goods and Services Tax applied to billing. Default rate is 18%.

### Guardian
A parent or guardian role that can view their linked student's activity and progress.

---

## I

### Inline Test
A test embedded within a chapter, positioned between pages using an `order` field.

### Institute
An educational organization (school, college, etc.) that operates under a partner. Institutes manage classrooms, teachers, and students.

### Invoice
A billing document generated for a partner's seat usage during a billing cycle. Paid through Razorpay.

---

## L

### Live Course
A course with `APPROVED` status that is accessible to users based on its visibility settings.

---

## M

### Merged
A course status indicating that a previous version has been replaced by an approved revision.

### Milestone
A progress checkpoint within a course (chapter or test). Students track completion against milestones. 100% milestone completion enables certificate generation.

---

## O

### Overall Intent Configuration
Configuration at the course level that defines evaluation criteria for AI-assisted test grading.

---

## P

### Page
A content unit within a chapter. Contains rich text, images, videos, and other media.

### Paisa
The smallest unit of Indian currency (1/100 of a Rupee). All monetary values in TinkerBunker are stored in paisa to avoid floating-point issues. Example: 100000 paisa = Rs 1000.

### Partner
An organization that operates a white-labeled instance of TinkerBunker. Partners manage institutes and can have custom branding.

### Partner URL
A custom domain assigned to a partner for white-label access.

### Pending Approval
The state of a user who has requested to join an institute but has not yet been approved by the institute admin.

### PendingApprovalGuard
A frontend guard that restricts pending users to only access the dashboard and login-related pages.

### Post-Test
An assessment placed at the end of a course to evaluate overall learning outcomes.

### Practice Test
A test that students can attempt multiple times for self-paced practice, with attempt tracking.

### Pre-Test
An assessment placed at the beginning of a course to gauge baseline knowledge.

### Price (Paisa)
The cost of a course or seat in paisa units. Only applicable when `is_paid` is true.

---

## R

### Razorpay
The payment gateway integrated with TinkerBunker for processing course payments and partner invoices.

### Referral Code
A coupon code that provides a discount on course purchases or seat pricing. Created by Sales users, requires approval before activation.

### Rejection Reason
The feedback provided by an Admin Publisher when rejecting a course, or by an institute admin when rejecting a join request.

### Remote (Physical)
A wireless clicker device used in Remote Quiz sessions. Each remote has a unique MAC address.

### Remote MAC ID
The unique hardware identifier of a physical remote device, used for student-to-remote mapping.

### Remote Quiz
A live quiz feature using physical USB receivers and wireless remote clickers for real-time classroom assessments.

### Revision
A copy of an approved course created for editing. The live version remains unchanged until the revision is approved.

### Role
A user type that determines access and capabilities on the platform. Users can hold multiple roles simultaneously.

---

## S

### Sales
A role responsible for managing partners and their relationships. Sales users are managed by Admin Publishers.

### Seat
A unit of access in the partner billing model. Partners purchase seats and allocate them to institutes.

### Seat Pool
The total, allocated, and free seat counts for a partner.

### Sub-Category
A second-level classification within a category (e.g., "Physics" under "Science").

### Sub-Partner
A partner operating under another partner, forming a hierarchical relationship. Sub-partners can have their own institutes and branding.

### Super Admin
The highest-privilege role with unrestricted access to all platform features, including category management and global pricing.

### Suspended
A billing status indicating overdue payment. Suspends all write operations for the partner's hierarchy.

### SuspendedPartnerGuard
A global backend guard that blocks write operations for partners with suspended billing cycles. The block cascades to all institutes, teachers, and students under the partner.

---

## T

### Teacher Test
A standalone test created by a teacher, independent of any course. Can be converted into assignments.

### Team Member
A meta-role for users operating under a primary account (Partner, Institute, Sales, or Admin Creator) with delegated permissions defined in the `controls` field.

### Team Type
The category of team a member belongs to: `partner`, `institute`, `sales`, or `admin_creator`.

### Test
An assessment containing questions. Types: `PRE_TEST`, `POST_TEST`, `INLINE_TEST`, `TEACHER_TEST`.

### Test Attempt Configuration
Settings controlling how many times a test can be attempted and whether it locks after max attempts.

---

## U

### USB Receiver
A hardware device that connects to a computer via USB and communicates wirelessly with student remotes during Remote Quiz sessions.

### User Role Entity
A database entity linking a user to a role at a specific institute, enabling multi-role and multi-institute membership.

---

## V

### Verification (Certificate)
The process of confirming a certificate's authenticity using its UUID. Performed cryptographically by comparing stored and regenerated signatures.

### Version
A numeric identifier tracking course iterations. New versions are linked to the original via `parent_course_id`.

### Visibility
Course access settings determined by `is_public` and `is_paid` flags.

---

## W

### Web Quiz
An online quiz session where students participate via their web browsers, providing an alternative to Remote Quiz without physical hardware.

### Webhook
An HTTP callback from Razorpay that notifies TinkerBunker of payment events (captured, failed, order paid).

### White Labeling
The ability for partners to brand the platform with their own logo, company name, and custom domain.

---

## Next Steps

- [FAQ](faq.md) — Common questions and answers
- [Troubleshooting](troubleshooting.md) — Issue resolution guides
