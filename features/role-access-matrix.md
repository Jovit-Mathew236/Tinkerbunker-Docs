# Role Access Matrix

A comprehensive reference of which features and platform sections are accessible to each role in TinkerBunker.

---

## Roles

TinkerBunker has **11 roles** (including team member as a meta-role):

| #  | Role              | Code              | Description                          |
| -- | ----------------- | ----------------- | ------------------------------------ |
| 1  | Public            | `public`          | Unauthenticated / public user        |
| 2  | Student           | `student`         | Enrolled learner                     |
| 3  | Teacher           | `teacher`         | Teaches classes, assigns tests       |
| 4  | Guardian          | `guardian`        | Parent/guardian of a student         |
| 5  | Institute         | `institute`       | School/organization admin            |
| 6  | Partner           | `partner`         | White-label platform operator        |
| 7  | Sales             | `sales`           | Manages partners                     |
| 8  | Admin Creator     | `admin_creator`   | Creates course content               |
| 9  | Admin Publisher   | `admin_publisher` | Reviews and publishes courses        |
| 10 | Super Admin       | `super_admin`     | Full system administrator            |
| 11 | Team Member       | `team_member`     | Delegated access (meta-role)         |

{% hint style="info" %}
**Team Member** is a meta-role that resolves to the actual team type: `partner`, `institute`, `sales`, or `admin_creator`. Team members have restricted access based on their `controls` JSONB permissions.
{% endhint %}

---

## Feature Access Matrix

Legend: **Y** = Full Access | **L** = Limited Access | **-** = No Access

| Feature                | Public | Student | Teacher | Guardian | Institute | Partner | Sales | Creator | Publisher | Super Admin |
| ---------------------- | :----: | :-----: | :-----: | :------: | :-------: | :-----: | :---: | :-----: | :-------: | :---------: |
| **Dashboard**          | -      | Y       | Y       | Y        | Y         | Y       | Y     | Y       | Y         | Y           |
| **Courses (Browse)**   | Y      | Y       | Y       | -        | Y         | Y       | Y     | Y       | Y         | Y           |
| **Courses (Create)**   | -      | -       | -       | -        | -         | -       | -     | Y       | -         | -           |
| **Courses (Review)**   | -      | -       | -       | -        | -         | -       | -     | -       | Y         | L           |
| **Courses (Assign)**   | -      | -       | -       | -        | -         | -       | Y     | -       | Y         | -           |
| **Course Enrollment**  | L      | Y       | -       | -        | -         | -       | -     | -       | -         | -           |
| **Tests (Course)**     | -      | Y       | -       | -        | -         | -       | -     | Y       | L         | -           |
| **Tests (Teacher)**    | -      | -       | Y       | -        | -         | -       | -     | -       | -         | -           |
| **Practice Tests**     | L      | Y       | Y       | -        | -         | -       | -     | -       | -         | -           |
| **Remote Quiz**        | -      | -       | Y       | -        | -         | -       | -     | -       | -         | -           |
| **Web Quiz**           | -      | Y       | Y       | -        | -         | -       | -     | -       | -         | -           |
| **Classrooms**         | -      | Y       | Y       | -        | Y         | -       | -     | -       | -         | -           |
| **Schools**            | -      | -       | -       | -        | -         | Y       | -     | -       | -         | -           |
| **Partners**           | -      | -       | -       | -        | -         | -       | Y     | -       | -         | -           |
| **Sub-Partners**       | -      | -       | -       | -        | -         | Y       | -     | -       | -         | -           |
| **Sales Management**   | -      | -       | -       | -        | -         | -       | -     | -       | Y         | -           |
| **Teams**              | -      | -       | -       | -        | Y         | Y       | Y     | Y       | -         | -           |
| **Stats (Student)**    | -      | Y       | -       | -        | -         | -       | -     | -       | -         | -           |
| **Stats (Teacher)**    | -      | -       | Y       | -        | -         | -       | -     | -       | -         | -           |
| **Stats (Institute)**  | -      | -       | -       | -        | Y         | -       | -     | -       | -         | -           |
| **Categories**         | -      | -       | -       | -        | -         | -       | -     | -       | -         | Y           |
| **Certificates**       | L      | Y       | -       | -        | -         | -       | -     | -       | -         | -           |
| **Cert Verification**  | Y      | Y       | Y       | Y        | Y         | Y       | Y     | Y       | Y         | Y           |
| **Billing**            | -      | -       | -       | -        | L         | Y       | -     | -       | -         | -           |
| **Global Pricing**     | -      | -       | -       | -        | -         | -       | -     | -       | -         | Y           |
| **Referral Codes**     | -      | -       | -       | -        | -         | -       | Y     | -       | -         | -           |
| **Favorites**          | -      | Y       | Y       | -        | -         | -       | -     | -       | -         | -           |
| **My Students**        | -      | -       | -       | Y        | -         | -       | -     | -       | -         | -           |
| **Approval Mgmt**     | -      | -       | -       | -        | Y         | -       | -     | -       | -         | -           |
| **White Labeling**     | -      | -       | -       | -        | -         | L       | -     | -       | -         | -           |

---

## Navigation Items by Role

| Role             | Navigation Items                                           |
| ---------------- | ---------------------------------------------------------- |
| Public           | Courses                                                    |
| Student          | Classroom, Courses, Stats                                  |
| Teacher          | Classroom, Courses, Tests, Stats                           |
| Guardian         | My Students                                                |
| Institute        | Classrooms, Courses, Teams*, Stats                         |
| Partner          | Courses, Schools, Teams*, Sub-Partners*                    |
| Sales            | Courses, Partners, Teams*                                  |
| Admin Creator    | Courses, Teams*                                            |
| Admin Publisher   | Courses, Sales                                            |
| Super Admin      | Courses, Categories                                        |

\* Teams and Sub-Partners are hidden for team members.

---

## Team Member Permissions by Team Type

| Permission              | Partner Team | Institute Team | Sales Team | Creator Team |
| ----------------------- | :----------: | :------------: | :--------: | :----------: |
| `school_operation`      | Y            | -              | -          | -            |
| `subpartner_operation`  | Y            | -              | -          | -            |
| `seat_operation`        | Y            | -              | -          | -            |
| `classroom_operation`   | -            | Y              | -          | -            |
| `course_operation`      | -            | -              | -          | Y            |
| `partner_operation`     | -            | -              | Y          | -            |
| `coupon_operation`      | -            | -              | Y          | -            |
| `course_assign_operation`| -           | -              | -          | -            |
| `price_operation`       | -            | -              | -          | -            |

---

## Guards Reference

| Guard                         | Protects                                     |
| ----------------------------- | -------------------------------------------- |
| `SuperAdminOnlyGuard`         | Categories, global pricing                   |
| `CourseStatusGuard`           | Course status transitions                    |
| `CourseOperationGuard`        | Course CRUD operations                       |
| `ContentAccessGuard`          | Content visibility                           |
| `TeamMemberPermissionGuard`   | Team member delegated actions                |
| `SalesRoleGuard`              | Sales-specific endpoints                     |
| `SalesAdminGuard`             | Admin publisher managing sales               |
| `SalesOwnershipGuard`         | Sales editing own profile                    |
| `SalesPartnerAssignmentGuard` | Sales assigning to their partners            |
| `ProfileOwnershipGuard`       | Users editing own profile                    |
| `PartnerInstituteAccessGuard` | Partner accessing their institutes           |
| `InstituteOwnershipGuard`     | Institute admin actions                      |
| `TeacherOwnershipGuard`       | Teacher-specific access                      |
| `TeacherPageAccessGuard`      | Teacher page visibility                      |
| `StudentOwnershipGuard`       | Student-specific access                      |
| `StudentPageAccessGuard`      | Student page visibility                      |
| `GuardianAuthGuard`           | Guardian authentication                      |
| `GuardianAccessGuard`         | Guardian viewing their students              |
| `AdminCreatorOwnershipGuard`  | Creator-specific access                      |
| `AdminPublisherOwnershipGuard`| Publisher-specific access                    |
| `ClassMentorGuard`            | Teacher is mentor of a class                 |
| `SuspendedPartnerGuard`       | Blocks writes for suspended billing          |
| `TeamMemberDeleteGuard`       | Team member removal                          |
| `TeamMemberOwnershipGuard`    | Team member management                       |
| `ViewPartnerProfileGuard`     | Viewing partner data                         |
| `ViewAllPartnerProfileGuard`  | Viewing all partner data                     |
| `PendingApprovalGuard`        | Frontend: restricts pending user routes      |

---

## Next Steps

- [Course Lifecycle](course-lifecycle.md) — How roles interact across course stages
- [Approval System](approval-system.md) — Institute approval workflow
- [White Labeling](white-labeling.md) — Partner branding features
