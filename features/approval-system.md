# Approval System

TinkerBunker uses an approval workflow to control who gets access to institute-level features.

---

## How It Works

When a student or teacher signs up through the Institute signup flow, their account is created but held in a **pending** state. The institute admin must approve them before they get full access.

---

## Approval Flow

| Step | What Happens |
|---|---|
| 1 | User signs up and selects an institute |
| 2 | User's request appears in the institute's pending queue |
| 3 | Institute admin reviews and approves or rejects |
| 4 | Approved users get full access to their role |

---

## Who Approves Whom

| Approver | Approves |
|---|---|
| Institute Admin | Students and Teachers |
| Partner | Institutes (via invitation) |
| Sales | Partners (via invitation) |
| Admin Publisher | Sales (via invitation) |

{% hint style="info" %}
Partners, Institutes, and Sales users cannot self-register. They must be invited by the role above them.
{% endhint %}
