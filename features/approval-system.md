# ✅ Approval System

New accounts need approval before full access.

---

## Flow

```mermaid
flowchart LR
    A[📝 Sign Up] --> B[📧 Verify Email]
    B --> C[⏳ Wait for Approval]
    C --> D{Decision}
    D -->|Approved| E[🟢 Full Access]
    D -->|Rejected| F[🔴 Access Denied]
```

---

## Key Points

- Email verification is **required** after sign-up
- An admin or partner reviews the account
- Approved users get full role-based access
- Rejected users are notified via email

---

{% hint style="warning" %}
Approval times depend on the institute or partner.
{% endhint %}
