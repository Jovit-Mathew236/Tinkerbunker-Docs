# Forgot Password

If you have forgotten your password, TinkerBunker provides an OTP-based reset flow. You do not need to be logged in to reset your password.

---

## Password Reset Flow

### Step 1: Navigate to the Forgot Password Page

1. Go to `/forgotpassword` or click the **Forgot Password?** link on the login page.

![Forgot Password Link](../.gitbook/assets/forgot-password-link.png)

### Step 2: Enter Your Email

1. Enter the **email address** associated with your TinkerBunker account.
2. Click **Send OTP**.

{% hint style="info" %}
The email must match an existing account. If no account is found for the email you entered, you will see an error message.
{% endhint %}

### Step 3: Check Your Email for the OTP

1. Open the email from TinkerBunker containing your one-time password (OTP).
2. The OTP is a **6-digit numeric code**.
3. The OTP is valid for a limited time (typically 10 minutes).

{% hint style="warning" %}
If you do not receive the OTP email, check your spam or junk folder. Ensure the email address is correct and try sending the OTP again. There may be a short cooldown between resend attempts.
{% endhint %}

### Step 4: Enter the OTP

1. Return to the TinkerBunker forgot password screen.
2. Enter the **6-digit OTP** in the verification field.
3. Click **Verify OTP**.

![OTP Entry Screen](../.gitbook/assets/otp-entry-screen.png)

### Step 5: Set a New Password

1. After successful OTP verification, you are presented with the password reset form.
2. Enter your **new password** (minimum 8 characters).
3. Enter the password again in the **Confirm Password** field.
4. Click **Reset Password**.

### Step 6: Log In

1. After the password is reset successfully, you are redirected to the login page.
2. Log in using your email and the **new password**.

{% hint style="success" %}
Your password has been updated. All existing sessions on other devices will be invalidated. You will need to log in again on any device where you were previously signed in.
{% endhint %}

---

## Summary of the Flow

| Step | Action | What Happens |
| --- | --- | --- |
| 1 | Navigate to `/forgotpassword` | Forgot password form is displayed |
| 2 | Enter email and click Send OTP | OTP is sent to the registered email |
| 3 | Enter the 6-digit OTP | OTP is verified server-side |
| 4 | Enter and confirm new password | Password is updated in the system |
| 5 | Log in with new password | Access is restored |

---

## Troubleshooting

| Issue | Solution |
| --- | --- |
| OTP not received | Check spam folder. Verify the email address. Wait for cooldown and resend. |
| OTP expired | Request a new OTP by clicking **Resend OTP**. Each new OTP invalidates the previous one. |
| Invalid OTP error | Ensure you are entering the most recent OTP. Copy-paste to avoid typos. |
| Password reset fails | Ensure the new password meets minimum requirements (8+ characters). Both fields must match. |
| Account not found | Verify you are using the correct email. You may have signed up with Google OAuth -- try logging in with Google instead. |

---

## Next Steps

- [Log in to your account](logging-in.md)
- [Return to Platform Overview](overview.md)
