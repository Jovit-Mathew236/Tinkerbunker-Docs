# ✅ Approve New Users

Review and respond to incoming user requests.

---

## 🔄 How It Works

```mermaid
flowchart LR
    A[User sends request] --> B[Request appears in Approvals]
    B --> C{Review details}
    C -->|Approve| D[User gets access]
    C -->|Reject| E[User is notified]
```

---

## 📝 Steps

1. Go to **Approvals** from the sidebar.
2. Review the user's name, role, and details.
3. Click **Approve** or **Reject**.

---

## 📌 Quick Tips

- Approved users can immediately access the institute.
- Rejected users receive a notification with the reason.

{% hint style="info" %}
You need the `approval_operation` flag to manage approvals.
{% endhint %}
