# Remote Quiz

TinkerBunker supports **live interactive quizzes** conducted in real time using physical remote/receiver devices. This feature transforms the classroom into an engaging, game-like assessment environment where students respond using handheld remotes and results are captured instantly.

---

## Overview

| Aspect | Description |
| --------------------- | ------------------------------------------------------------------------------ |
| **What It Is** | A live quiz session where questions are projected and students respond in real time using physical receiver devices. |
| **Hardware Required** | Physical remote devices (student handhelds) and a USB receiver connected to the teacher's computer. |
| **Use Case** | In-class quizzes, quick assessments, revision games, interactive lectures. |

<figure><img src="../.gitbook/assets/remote-quiz-session.png" alt="Remote Quiz Session"><figcaption></figcaption></figure>

---

## Hardware Setup

Before starting a remote quiz, ensure the hardware is ready.

### Requirements

| Component | Description |
| ---------------------- | -------------------------------------------------------------------- |
| **Student Remotes** | Handheld devices with numbered buttons for answering questions. |
| **USB Receiver** | A receiver device plugged into the teacher's computer that captures signals from student remotes. |
| **Teacher's Computer** | A computer running TinkerBunker in a web browser with the USB receiver connected. |
| **Projector/Display** | A screen visible to all students for displaying questions. |

{% tabs %}
{% tab title="Setting Up the Receiver" %}
1. Plug the USB receiver into the teacher's computer.
2. Ensure the receiver is recognized by the system (driver installation may be required on first use).
3. Open TinkerBunker and navigate to **Tests → Remote Quiz**.
4. The system should detect the connected receiver automatically.
{% endtab %}

{% tab title="Distributing Remotes" %}
1. Hand out one remote device to each student.
2. Each remote has a unique ID number.
3. Map each remote ID to a student in the quiz session setup.
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Ensure all remotes have working batteries before starting the session. A non-responsive remote will prevent a student from participating.
{% endhint %}

---

## Setting Up a Quiz Session

{% tabs %}
{% tab title="Steps" %}
1. Navigate to **Tests** in the navigation bar.
2. Click **Remote Quiz** (or **Start Remote Quiz**).
3. Select an existing test to use for the quiz, or create a new one.
4. Configure session settings:
   - **Time per question** — How long students have to answer each question.
   - **Show correct answer** — Whether to reveal the correct answer after each question.
   - **Scoring mode** — Points for correct answers; optionally, negative marking for wrong answers.
5. Map student remotes to student accounts (by remote device ID).
6. Click **Start Session** to begin.
{% endtab %}

{% tab title="Screenshot" %}
<figure><img src="../.gitbook/assets/remote-quiz-setup.png" alt="Remote Quiz Setup"><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

---

## Session Configuration

| Setting | Description |
| ------------------------- | -------------------------------------------------------------------- |
| **Test Selection** | Choose which test's questions to use for the quiz. |
| **Time Per Question** | Duration (in seconds) allowed for each question. |
| **Show Correct Answer** | Reveals the answer after each question for instant feedback. |
| **Scoring Mode** | Standard (points for correct only) or negative marking enabled. |
| **Remote-Student Mapping** | Associates each physical remote ID with a student in the system. |

---

## Running the Quiz

Once the session starts, the quiz flows as follows:

1. **Question Display** — The current question is projected on screen with answer options.
2. **Response Window** — A countdown timer starts. Students press the corresponding button on their remote.
3. **Response Capture** — The receiver captures each remote's input in real time. A progress indicator shows how many students have responded.
4. **Answer Reveal** — (If enabled) The correct answer is highlighted on screen.
5. **Score Update** — The live leaderboard updates with current standings.
6. **Next Question** — You advance to the next question manually or it auto-advances after the timer.

{% hint style="info" %}
You control the pace of the quiz. You can pause between questions to discuss answers or provide explanations before moving to the next one.
{% endhint %}

---

## Managing Responses in Real Time

During the quiz, the teacher's screen shows a real-time dashboard:

| Element | Description |
| ------------------------ | ------------------------------------------------------------------- |
| **Response Counter** | Shows "X of Y students have responded" for the current question. |
| **Response Distribution**| A bar chart showing how many students chose each answer option. |
| **Live Leaderboard** | Running scoreboard ranking students by total points. |
| **Student List** | Indicates which students have responded and which have not. |

<figure><img src="../.gitbook/assets/remote-quiz-live.png" alt="Real-Time Response Dashboard"><figcaption></figcaption></figure>

---

## After the Quiz

When all questions are completed:

1. The final leaderboard is displayed.
2. Results are saved to TinkerBunker automatically.
3. You can:
   - **Export Results** — Download the quiz results as a report.
   - **Review Responses** — See each student's answer for every question.
   - **Release Scores** — Make results available to students in their stats.

{% hint style="info" %}
Remote quiz results are integrated with the student stats system. Students can see their remote quiz performance under their **Stats** section.
{% endhint %}

---

## Troubleshooting

| Issue | Resolution |
| ------------------------------- | -------------------------------------------------------------------- |
| Receiver not detected | Unplug and re-plug the USB receiver. Ensure drivers are installed. |
| Remote not responding | Check the remote's battery. Try pressing buttons firmly. |
| Duplicate responses | Ensure each remote ID is mapped to only one student. |
| Student missing from mapping | Add the student to the session and assign a spare remote. |

{% hint style="warning" %}
Always conduct a quick test with the remotes before starting a formal quiz session to verify all devices are working properly.
{% endhint %}
