# Enrolling in Courses

This guide explains how public users can enroll in TinkerBunker courses, including both free and paid enrollment flows.

---

## Prerequisites

To enroll in a course, you need:

1. A TinkerBunker account (sign up via the registration page)
2. For institute courses: approved membership at an institute

{% hint style="info" %}
Public courses can be enrolled in by any registered user. Institute-specific courses require enrollment through your institute.
{% endhint %}

---

## Enrollment Types

{% tabs %}
{% tab title="Free Public Courses" %}
### Enrolling in a Free Course

1. Browse the [Course Catalog](browsing-courses.md)
2. Click on a course to view its details
3. Click **Enroll**
4. You are immediately enrolled and can start learning

No payment is required. You get full access to:
- All chapters and pages
- Embedded tests (pre-test, post-test, inline tests)
- Progress tracking
- Certificate upon completion

![Free Course Enrollment](../.gitbook/assets/free-enrollment.png)
{% endtab %}

{% tab title="Paid Public Courses" %}
### Enrolling in a Paid Course

1. Browse the [Course Catalog](browsing-courses.md)
2. Click on a course showing a price tag
3. Review the course details and pricing
4. Click **Buy Now**
5. The **Razorpay checkout** modal opens
6. Choose your payment method:
   - UPI
   - Credit / Debit Card
   - Net Banking
   - Wallets
7. Complete the payment
8. Payment is verified automatically
9. You are enrolled upon successful payment

### Payment Verification

The system verifies your payment through:

1. **Razorpay Signature Validation** — Ensures the payment response is authentic
2. **Order Matching** — Confirms the payment matches the course order
3. **Enrollment Creation** — Creates your enrollment record with payment references

### Applying a Coupon Code

If you have a referral/coupon code:

1. Enter the code in the coupon field before clicking **Buy Now**
2. The system calculates the discounted price
3. You see a breakdown: original price, discount, GST, final price
4. Proceed with payment at the discounted rate

{% hint style="info" %}
Coupon codes are validated for: existence, expiry date, usage limits, and applicability. Invalid codes show an error message.
{% endhint %}
{% endtab %}

{% tab title="Institute Courses" %}
### Enrolling via Institute

Students enrolled at an institute access courses assigned by their partner/institute:

1. Log in to your institute account
2. Navigate to **Courses** or **Classroom**
3. Courses assigned to your institute are automatically available
4. Click on a course to begin

No separate enrollment step is needed — courses are assigned at the partner/institute level.

### Institute Enrollment Prerequisite

Before accessing institute courses, you need:

1. Sign up and request to join an institute
2. Select your role (Student or Teacher)
3. Wait for institute admin approval
4. Once approved, you gain access to the institute's courses

See [Approval System](../features/approval-system.md) for details on the approval workflow.
{% endtab %}
{% endtabs %}

---

## Enrollment Record

Each enrollment creates a record with the following data:

| Field                 | Description                              |
| --------------------- | ---------------------------------------- |
| User ID               | Your account identifier                  |
| Course ID             | The enrolled course                      |
| Enrollment Status     | Active / Completed / Cancelled           |
| Razorpay Order ID     | Payment reference (paid courses only)    |
| Razorpay Payment ID   | Payment transaction ID (paid courses)    |
| Enrolled At           | Date and time of enrollment              |

---

## After Enrollment

Once enrolled, you can:

### Track Progress

- View completion percentage on the course card
- See milestone progress for each chapter
- Track test scores

### Take Tests

- **Pre-Test** — Assess your initial knowledge
- **Inline Tests** — Test understanding during chapters
- **Post-Test** — Final assessment after completion
- **Practice Tests** — Additional practice with attempt tracking

### Earn a Certificate

Upon completing all milestones (100% progress):

1. A certificate is automatically generated
2. Download it as a PDF
3. Share the public verification link

See [Certificates](../features/certificates.md) for full details.

---

## Troubleshooting Enrollment

| Issue                        | Solution                                             |
| ---------------------------- | ---------------------------------------------------- |
| Payment failed               | Retry payment or use a different payment method      |
| Course not visible           | Check if the course is public; private courses need assignment |
| Cannot enroll                | Ensure you are logged in with a registered account   |
| Institute course unavailable | Confirm your institute membership is approved        |
| Coupon code rejected         | Verify the code is valid, not expired, and has remaining uses |

---

## Next Steps

- [Browsing Courses](browsing-courses.md) — Find your next course
- [Verify Certificate](verify-certificate.md) — Share and verify your achievements
