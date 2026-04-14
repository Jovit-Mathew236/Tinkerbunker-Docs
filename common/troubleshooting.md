# Troubleshooting

Common issues and solutions organized by role and feature area.

---

## General Issues

### Cannot Log In

| Symptom                        | Solution                                                |
| ------------------------------ | ------------------------------------------------------- |
| "Invalid credentials" error    | Verify email and password. Use **Forgot Password** to reset. |
| Account locked                 | Contact your administrator or support.                  |
| Redirected to login repeatedly | Clear browser cookies and cache. Try incognito mode.    |
| White-label login not loading  | Check if the custom domain DNS is properly configured.  |

### Session Issues

| Symptom                     | Solution                                          |
| --------------------------- | ------------------------------------------------- |
| Logged out unexpectedly     | Session may have expired. Log in again.           |
| Role switcher not working   | Refresh the page. Verify you have multiple roles. |
| Features missing after login| Check your active role via the profile dropdown.  |

---

## Student Issues

### Course Access

| Symptom                              | Solution                                          |
| ------------------------------------ | ------------------------------------------------- |
| Cannot see any courses               | Verify your institute membership is approved.     |
| Course shows "Enroll" but fails      | Check if the course requires payment.             |
| Progress not saving                  | Ensure stable internet connection. Refresh page.  |
| Cannot access a course after enrollment | Course may have been unpublished. Contact admin. |

### Tests

| Symptom                         | Solution                                               |
| ------------------------------- | ------------------------------------------------------ |
| Test shows "Locked"             | Maximum attempts reached. Contact your teacher.        |
| Cannot submit test answers      | Check if the timer has expired. Refresh and retry.     |
| Practice test not available     | Verify you have remaining attempts.                    |
| Score not displayed             | Wait for evaluation (descriptive tests take longer).   |

### Certificates

| Symptom                        | Solution                                               |
| ------------------------------ | ------------------------------------------------------ |
| Certificate not generated      | Ensure 100% course completion (all milestones done).   |
| PDF download fails             | Try a different browser. Check popup blockers.         |
| Certificate shows wrong name   | Contact your institute admin to update your profile.   |

---

## Teacher Issues

### Test Management

| Symptom                            | Solution                                          |
| ---------------------------------- | ------------------------------------------------- |
| Cannot create a teacher test       | Verify you are logged in with the Teacher role.   |
| Assignment not visible to students | Ensure the assignment is in **Published** status. |
| AI evaluation stuck in "Processing"| Check processing status. May need to retry.       |
| PDF upload failing                 | Verify file size limits. Use PDF format only.     |

### Remote Quiz

| Symptom                         | Solution                                                 |
| ------------------------------- | -------------------------------------------------------- |
| USB receiver not detected       | Reconnect USB. Try a different port. Restart browser.    |
| Remotes not pairing             | Press and hold pairing button. Replace battery if needed.|
| Student responses not received  | Check student-to-remote mapping. Verify remote is paired.|
| Quiz session stuck              | Refresh the page. Restart the quiz session.              |
| Slow response collection        | Move receiver closer to students. Reduce interference.   |

---

## Institute Admin Issues

### Approval Management

| Symptom                           | Solution                                           |
| --------------------------------- | -------------------------------------------------- |
| Cannot see pending requests       | Navigate to the approval section. Check filters.   |
| Approve button not working        | Verify you have institute admin permissions.       |
| Student not gaining access        | Ensure approval was successful. Ask student to refresh. |
| Cannot reject without reason      | Rejection reason is required. Enter feedback text. |

### Classroom Management

| Symptom                     | Solution                                          |
| --------------------------- | ------------------------------------------------- |
| Cannot create a classroom   | Verify `classroom_operation` permission.          |
| Students not appearing      | Check if students are approved and enrolled.      |
| Course not available        | Verify the course is assigned to your partner.    |

---

## Partner Issues

### Billing

| Symptom                            | Solution                                            |
| ---------------------------------- | --------------------------------------------------- |
| Yellow billing banner              | You have a pending invoice. Navigate to billing.    |
| Red billing banner                 | Payment is overdue. Complete payment immediately.   |
| Cannot perform any actions         | Account is suspended. Pay outstanding invoices.     |
| Payment failed at Razorpay         | Try a different payment method. Check bank limits.  |
| Invoice amount seems incorrect     | Review invoice line items. Contact support if wrong.|

### Seat Management

| Symptom                          | Solution                                            |
| -------------------------------- | --------------------------------------------------- |
| Cannot allocate seats            | Check your free seat count. Purchase more if needed.|
| Institute shows "No seats"       | Allocate seats from your seat pool.                 |
| Seat count mismatch              | Review allocation history. Contact support.         |

### White Labeling

| Symptom                         | Solution                                             |
| ------------------------------- | ---------------------------------------------------- |
| Logo not appearing on login     | Verify `partner_url` matches your domain.            |
| Cannot upload logo              | Check subscription includes `allow_logo_upload`.     |
| Custom domain not working       | Verify DNS CNAME record. Allow 24-48 hours.         |
| Wrong branding displayed        | Clear browser cache. Verify partner URL config.      |

---

## Sales Issues

### Partner Management

| Symptom                          | Solution                                          |
| -------------------------------- | ------------------------------------------------- |
| Cannot create a partner          | Verify `partner_operation` permission.            |
| Duplicate email error            | The email is already in use. Use a different one. |
| Partner not appearing in list    | Refresh the page. Check filters.                  |
| Cannot assign courses            | Courses must be in `APPROVED` status.             |

### Team Management

| Symptom                     | Solution                                                |
| --------------------------- | ------------------------------------------------------- |
| Team member cannot log in   | Verify invitation was accepted. Resend if needed.       |
| Team member sees limited UI | This is expected. Team members have restricted access.  |
| Cannot add team member      | Verify you are the primary account (not a team member). |

---

## Admin Creator Issues

### Course Creation

| Symptom                            | Solution                                           |
| ---------------------------------- | -------------------------------------------------- |
| Cannot create a course             | Verify `course_operation` permission.              |
| Content not saving                 | Check internet connection. Try saving again.       |
| Sync Content fails                 | Ensure all chapters have valid content.            |
| Cannot submit for review           | Course must be in `DRAFT` status.                  |
| Course stuck in "Pending Review"   | Wait for Admin Publisher to review.                |

### Import Issues

| Symptom                  | Solution                                               |
| ------------------------ | ------------------------------------------------------ |
| Import fails             | Verify file format matches the expected schema.        |
| Imported content missing | Check the import file for completeness.                |

---

## Admin Publisher Issues

### Review Process

| Symptom                         | Solution                                            |
| ------------------------------- | --------------------------------------------------- |
| No courses in Review tab        | No courses are currently pending review.            |
| Cannot approve course           | Verify you have Admin Publisher role active.         |
| Approval not taking effect      | Check for errors. Refresh and try again.            |
| Rejected course reappearing     | Creator has resubmitted. Review again.              |

---

## Super Admin Issues

### Category Management

| Symptom                       | Solution                                           |
| ----------------------------- | -------------------------------------------------- |
| Cannot create category        | Category names must be unique.                     |
| Cannot delete category        | Ensure no courses are assigned to the category.    |
| Categories page not loading   | Verify you are logged in as Super Admin.           |

---

## Performance Issues

| Symptom                       | Solution                                               |
| ----------------------------- | ------------------------------------------------------ |
| Pages loading slowly          | Check internet connection. Clear browser cache.        |
| Images not loading            | Check if image URLs are accessible. Retry.             |
| API errors (500)              | Server issue. Wait and retry. Contact support if persistent. |
| Timeout errors                | Large operations may take time. Retry after a moment.  |

---

## Next Steps

- [FAQ](faq.md) — Frequently asked questions
- [Glossary](glossary.md) — Platform terminology
