---
description: Managing remote receiver devices for live quiz sessions within your institute.
---

# Remote Devices

Remote devices are physical receiver units used during live quiz sessions. They allow students to submit answers in real-time using handheld clickers or paired devices. As an institute admin, you manage the registration, configuration, and monitoring of these devices.

---

## What Are Remote Devices?

A remote device (receiver) is a hardware unit connected to the institute's network that:

- Captures student responses during live quizzes.
- Transmits answers to the platform in real-time.
- Enables interactive, classroom-based assessment sessions.

<figure><img src="../.gitbook/assets/institute-remote-device-setup.png" alt="Remote Device Setup"><figcaption><p>Remote receiver device connected and ready for a live quiz session</p></figcaption></figure>

---

## Viewing Registered Devices

1. Navigate to **Dashboard → Remote Devices**.
2. The device list shows all registered receivers.

| Column           | Description                                         |
| ---------------- | --------------------------------------------------- |
| **Device Name**  | A friendly label for the device.                    |
| **Device ID**    | Unique hardware identifier.                         |
| **Classroom**    | The classroom this device is assigned to (if any).  |
| **Status**       | Online, Offline, or Error.                          |
| **Last Active**  | Timestamp of the last communication from the device.|

---

## Registering a New Device

1. Go to **Dashboard → Remote Devices**.
2. Click **Add Device**.
3. Enter the device details:

| Field            | Required | Description                                           |
| ---------------- | -------- | ----------------------------------------------------- |
| **Device Name**  | Yes      | A human-readable label (e.g., "Receiver — Room 101"). |
| **Device ID**    | Yes      | The hardware ID printed on the device or its packaging.|
| **Classroom**    | No       | Optionally assign to a classroom immediately.         |

4. Click **Register**.

{% hint style="info" %}
The device must be powered on and connected to the network before it can be verified. After registration, the platform sends a handshake ping to confirm connectivity.
{% endhint %}

---

## Assigning a Device to a Classroom

Each device can be assigned to a specific classroom for organized live quiz management:

1. From the device list, click **Edit** on the target device.
2. Select a classroom from the **Classroom** dropdown.
3. Click **Save**.

{% hint style="warning" %}
A device can only be assigned to one classroom at a time. To reassign, update the classroom field — the previous association is automatically removed.
{% endhint %}

---

## Setting Up a Live Quiz Session

Once a device is registered and assigned:

1. The teacher opens a **Live Quiz** within the assigned classroom.
2. The platform detects the registered receiver and establishes a connection.
3. Students use their clickers or paired devices to submit responses.
4. Responses are captured in real-time and displayed on the teacher's screen.

### Troubleshooting Connectivity

If a device shows **Offline** or **Error** status:

{% tabs %}
{% tab title="Check Network" %}
- Verify the device is powered on.
- Confirm it is connected to the institute's local network (Wi-Fi or Ethernet).
- Ensure the network allows outbound connections to the platform servers.
{% endtab %}

{% tab title="Re-register" %}
- Remove the device from the list.
- Power cycle the device.
- Re-register using the same Device ID.
{% endtab %}

{% tab title="Contact Support" %}
If the above steps do not resolve the issue:
- Note the Device ID and error status.
- Contact platform support with the details.
{% endtab %}
{% endtabs %}

---

## Removing a Device

1. Go to **Dashboard → Remote Devices**.
2. Click the **Remove** icon next to the device.
3. Confirm the removal.

{% hint style="danger" %}
Removing a device immediately disconnects it from the platform. Any in-progress live quiz session using that device will lose the ability to capture responses from it.
{% endhint %}

---

## Related

- [Dashboard](dashboard.md)
- [Managing Classrooms](managing-classrooms.md)
