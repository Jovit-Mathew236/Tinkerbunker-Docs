# Verify Certificate

TinkerBunker provides public certificate verification that allows anyone to confirm the authenticity of a certificate — no login required.

---

## Overview

Every certificate issued by TinkerBunker has a unique UUID. Anyone with this UUID can verify the certificate's authenticity through a public verification page.

{% hint style="info" %}
Certificate verification is a **public feature** — no authentication or account is needed. The verification page is accessible to anyone with the certificate UUID.
{% endhint %}

---

## How to Verify a Certificate

### Step 1: Obtain the Certificate UUID

The certificate UUID is printed on the certificate document. It appears as a unique identifier in the format:

```
xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

### Step 2: Visit the Verification Page

Navigate to:

```
https://your-domain.com/verify-certificate/{uuid}
```

Replace `{uuid}` with the actual certificate UUID.

### Step 3: View Verification Results

The verification page displays one of two results:

{% tabs %}
{% tab title="Valid Certificate" %}
A green verification badge with the following details:

| Field               | Description                         |
| ------------------- | ----------------------------------- |
| Status              | "Certificate Verified" (green)      |
| Student Name        | Name of the certificate holder      |
| Course Name         | Name of the completed course        |
| Overall Percentage  | Score achieved in the course        |
| Completion Date     | Date the course was completed       |
| Certificate UUID    | Unique identifier for reference     |

<figure><img src="../.gitbook/assets/certificate-verified.png" alt="Valid Certificate Verification"><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Invalid Certificate" %}
A red error badge indicating:

| Field   | Description                                |
| ------- | ------------------------------------------ |
| Status  | "Invalid Certificate" (red)                |
| Message | Explanation of why verification failed     |

Possible reasons for invalid certificates:
- UUID does not exist in the system
- Certificate has been revoked (`is_valid: false`)
- Certificate data has been tampered with (signature mismatch)
{% endtab %}
{% endtabs %}

---

## Verification Technology

TinkerBunker uses cryptographic verification to ensure certificate authenticity:

### How It Works

1. **Certificate Creation** — When a certificate is issued:
   - A canonical JSON string is created from the certificate data
   - The string is hashed using **SHA-256**
   - The hash is digitally signed using **HMAC-SHA256** with a secret key
   - Both the hash (`certificate_data_hash`) and signature (`digital_signature`) are stored

2. **Verification** — When a certificate is verified:
   - The system retrieves the certificate by UUID
   - Recreates the hash from the stored data
   - Regenerates the expected signature
   - Compares the generated signature with the stored signature
   - Checks the `is_valid` flag
   - Returns verification result

{% hint style="info" %}
This cryptographic process ensures that any tampering with certificate data (name, course, score, date) is detected during verification.
{% endhint %}

---

## API Endpoints

For developers integrating certificate verification:

| Endpoint                              | Method | Auth Required | Description              |
| ------------------------------------- | ------ | ------------- | ------------------------ |
| `/api/v1/certificates/verify/{uuid}`  | GET    | No            | Verify certificate       |
| `/api/v1/certificates/public/{uuid}`  | GET    | No            | View certificate details |

### Verification Response

```json
{
  "is_valid": true,
  "certificate": {
    "student_name": "John Doe",
    "course_name": "Introduction to Physics",
    "overall_percentage": 87.5,
    "completion_date": "2024-03-15",
    "certificate_uuid": "abc123-..."
  },
  "message": "Certificate is valid and verified"
}
```

---

## Sharing a Certificate

Certificate holders can share their verification link:

1. Copy the verification URL from the certificate or profile
2. Share via email, social media, or embed in a resume
3. Recipients can click the link to instantly verify

---

## Next Steps

- [Browsing Courses](browsing-courses.md) — Discover available courses
- [Enrolling in Courses](enrolling.md) — Start your learning journey
