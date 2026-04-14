# Certificates

TinkerBunker automatically generates digitally signed certificates when students complete courses. Certificates can be downloaded as PDFs and verified publicly without authentication.

---

## Overview

| Feature                  | Description                                          |
| ------------------------ | ---------------------------------------------------- |
| Auto-generation          | Certificates are created upon course completion       |
| Digital signatures       | HMAC-SHA256 ensures tamper detection                  |
| PDF download             | Downloadable certificate in PDF format                |
| Public verification      | Anyone can verify via UUID — no login required        |
| Idempotent generation    | Requesting a certificate twice returns the same one   |

---

## Certificate Generation

### Eligibility

A certificate is generated when a student achieves **100% course progress** with a `COMPLETED` status. This means:

- All chapters have been viewed
- All required tests have been attempted
- All milestones are marked as complete

### Generation Flow

```
Student completes course (100% progress)
            │
            ▼
System validates completion
            │
            ▼
Checks for existing certificate (idempotent)
            │
        ┌───┴───┐
        ▼       ▼
    Exists    New
    Return    Generate
    existing      │
                  ▼
            Create UUID
                  │
                  ▼
            Build canonical data string (JSON)
                  │
                  ▼
            Hash with SHA-256
                  │
                  ▼
            Sign with HMAC-SHA256
                  │
                  ▼
            Save certificate
                  │
                  ▼
            Return certificate
```

### Two Generation Paths

{% tabs %}
{% tab title="Institute Students" %}
For students enrolled through an institute:

**Endpoint:** `POST /api/v1/certificates`

**Request:**
```json
{
  "student_id": "student-uuid",
  "class_id": "class-uuid",
  "course_id": "course-uuid"
}
```

The system uses the student's profile (linked to their institute) to generate the certificate.
{% endtab %}

{% tab title="Public Users" %}
For public users who enrolled directly:

**Endpoint:** `POST /api/v1/certificates`

**Request:**
```json
{
  "user_id": "user-uuid",
  "course_id": "course-uuid"
}
```

The system uses the user's account profile to generate the certificate.
{% endtab %}
{% endtabs %}

---

## Certificate Data

Each certificate contains:

| Field                  | Description                                     |
| ---------------------- | ----------------------------------------------- |
| `certificate_uuid`     | Unique public identifier                        |
| `student_name`         | Name of the certificate holder                  |
| `course_name`          | Name of the completed course                    |
| `completion_date`      | Date the course was completed                   |
| `issue_date`           | Date the certificate was issued                 |
| `overall_percentage`   | Score achieved in the course                    |
| `certificate_data_hash`| SHA-256 hash of the certificate data            |
| `digital_signature`    | HMAC-SHA256 signature for verification          |
| `is_valid`             | Whether the certificate is currently valid      |

---

## Downloading Certificates

### As a Student

1. Navigate to your **Profile** or **Certificates** section
2. View your earned certificates
3. Click **Download PDF** on any certificate
4. A PDF file is generated and downloaded

**Endpoint:** `GET /api/v1/certificates/{id}/download`

### Viewing All Certificates

| For                | Endpoint                                       |
| ------------------ | ---------------------------------------------- |
| Institute Student  | `GET /api/v1/certificates/student/{studentId}` |
| Public User        | `GET /api/v1/certificates/user/{userId}`       |

---

## Public Verification

Anyone can verify a certificate's authenticity using the public verification page.

### Verification URL

```
https://your-domain.com/verify-certificate/{certificate_uuid}
```

{% hint style="info" %}
No login or account is required to verify a certificate. The verification page is completely public.
{% endhint %}

### How Verification Works

1. The system retrieves the certificate by UUID
2. Recreates the canonical data string from stored fields
3. Recomputes the SHA-256 hash
4. Regenerates the HMAC-SHA256 signature using the server's secret key
5. Compares the generated signature with the stored signature
6. Checks the `is_valid` flag
7. Returns the verification result

### Verification Results

| Result       | Display                  | Meaning                           |
| ------------ | ------------------------ | --------------------------------- |
| Valid        | Green "Verified" badge   | Certificate is authentic          |
| Invalid      | Red "Invalid" badge      | Certificate failed verification   |

### Reasons for Invalid Status

- Certificate UUID does not exist
- Certificate has been manually revoked (`is_valid: false`)
- Certificate data has been tampered with (hash/signature mismatch)
- Server secret key has been rotated (rare edge case)

---

## Security

### Cryptographic Process

1. **Hashing:** A canonical JSON string of certificate data is hashed with **SHA-256**
   - This creates a fixed-length fingerprint of the certificate data

2. **Signing:** The hash is signed with **HMAC-SHA256** using `CERTIFICATE_SIGNATURE_SECRET`
   - This proves the certificate was issued by the TinkerBunker server
   - Only the server with the secret key can produce valid signatures

3. **Verification:** The same process is repeated and compared
   - Any change to the certificate data produces a different hash
   - A different hash produces a different signature
   - Mismatch = tampering detected

{% hint style="warning" %}
The `CERTIFICATE_SIGNATURE_SECRET` is a server-side secret. It must never be exposed. If compromised, all existing certificates' signatures would need to be regenerated.
{% endhint %}

---

## API Reference

| Endpoint                                     | Method | Auth     | Description              |
| -------------------------------------------- | ------ | -------- | ------------------------ |
| `/api/v1/certificates`                       | POST   | Required | Generate a certificate   |
| `/api/v1/certificates/{id}/download`         | GET    | Required | Download certificate PDF |
| `/api/v1/certificates/student/{studentId}`   | GET    | Required | List student certificates|
| `/api/v1/certificates/user/{userId}`         | GET    | Required | List user certificates   |
| `/api/v1/certificates/verify/{uuid}`         | GET    | None     | Verify certificate       |
| `/api/v1/certificates/public/{uuid}`         | GET    | None     | View certificate data    |

---

## Next Steps

- [Verify Certificate](../public/verify-certificate.md) — Public verification guide
- [Course Lifecycle](course-lifecycle.md) — How courses lead to certification
- [Test System](test-system.md) — Tests that contribute to completion
