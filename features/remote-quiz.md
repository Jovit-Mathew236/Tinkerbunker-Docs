# Remote Quiz

Remote Quiz is TinkerBunker's live quiz feature that uses **physical USB receiver hardware** and **student remote clickers** for real-time, interactive classroom assessments.

---

## Overview

The Remote Quiz system connects physical remote devices (clickers) to the platform via USB receivers. Teachers run live quiz sessions where students respond using their assigned remotes, and results are displayed in real-time.

```
Student Remote (Clicker)  ──wireless──►  USB Receiver  ──USB──►  Teacher's Computer
                                                                      │
                                                                      ▼
                                                              TinkerBunker Platform
                                                                      │
                                                                      ▼
                                                           Real-time Results Display
```

---

## Hardware Requirements

| Component        | Description                                         |
| ---------------- | --------------------------------------------------- |
| USB Receiver     | Plugs into the teacher's computer via USB            |
| Student Remotes  | Wireless clickers, each with a unique MAC address    |
| Teacher Remote   | Optional teacher-specific remote for control         |
| Computer         | Teacher's device running the TinkerBunker web app    |

### Remote Types

| Type      | Purpose                                    |
| --------- | ------------------------------------------ |
| `student` | Used by students to submit answers         |
| `teacher` | Used by the teacher to control quiz flow   |

Each remote is identified by a unique `remote_mac_id` and is bound to a specific institute.

---

## Setup

### Step 1: Register Remotes

Before running a quiz, remotes must be registered in the system:

1. Navigate to remote management settings
2. Click **Add Remotes**
3. The system detects connected USB receivers
4. Pair each physical remote by pressing a button on it
5. The remote's MAC address is captured and registered
6. Assign each remote as `student` or `teacher` type

![Add Remotes Modal](../.gitbook/assets/add-remotes-modal.png)

### Step 2: Map Students to Remotes

Each student must be mapped to a specific remote clicker:

1. Go to the student mapping interface
2. View the list of students in the class
3. Assign a remote (by MAC address) to each student
4. The mapping creates a `StudentMapping` record:

| Field             | Description                        |
| ----------------- | ---------------------------------- |
| Student ID        | The student being mapped           |
| Remote MAC ID     | The physical remote's MAC address  |
| Institute ID      | The institute context              |

{% hint style="warning" %}
Each remote can only be mapped to one student at a time. Reassigning a remote automatically unmaps the previous student.
{% endhint %}

### Step 3: Verify Receiver Connection

1. Click **Check Receiver**
2. The system verifies the USB receiver is connected and responsive
3. A green indicator confirms the connection
4. If not detected, check the USB connection and try again

---

## Running a Remote Quiz Session

### Quiz Flow Steps

The remote quiz follows a step-by-step flow managed by the Redux state:

```
1. Receiver Selection
       │
       ▼
2. Student Mapping
       │
       ▼
3. Quiz Ready
       │
       ▼
4. Quiz Active
       │
       ▼
5. Question Response (per question)
       │
       ▼
6. Question Results (per question)
       │
       ▼
7. Quiz Complete
```

---

### Step 1: Receiver Selection

1. Open the Remote Quiz interface
2. The system detects available USB receivers
3. Select the receiver to use for this session
4. Confirm the selection

### Step 2: Student Mapping

1. Review the student-to-remote mapping
2. Verify all participating students are mapped
3. Unmapped students cannot participate
4. Click **Continue** when mapping is complete

### Step 3: Quiz Ready

1. Select the test to use for the quiz
2. Review quiz settings (time per question, total questions)
3. Ensure all students have their remotes ready
4. Click **Start Quiz**

### Step 4: Quiz Active

The quiz is now live:

1. The first question is displayed on the teacher's screen (projected to the class)
2. A timer counts down for each question
3. Students press buttons on their remotes to submit answers

### Step 5: Question Response

During each question:

- The system receives responses from remotes in real-time
- Response data includes:

| Data Point     | Description                               |
| -------------- | ----------------------------------------- |
| Student ID     | Who submitted the answer                  |
| Remote MAC ID  | Which remote was used                     |
| Answer         | The selected option                       |
| Response Time  | Time taken to respond (milliseconds)      |

- A live counter shows how many students have responded
- Responses are collected in **batches** for efficiency

### Step 6: Question Results

After the time expires or all students have responded:

1. The correct answer is revealed
2. Response distribution is shown (how many chose each option)
3. Per-student results are available
4. Click **Next Question** to proceed

### Step 7: Quiz Complete

After the last question:

1. Overall quiz results are displayed
2. Student rankings by score
3. Per-question analytics
4. Session data is saved for review

---

## Batch Submission

Remote responses are collected in batches for performance:

| Field                | Description                              |
| -------------------- | ---------------------------------------- |
| `quiz_session_id`    | The active quiz session                  |
| `question_id`        | Current question being answered          |
| `responses`          | Array of `{ student_id, answer, time }`  |

The batch submission system ensures reliable data collection even with many simultaneous responses.

---

## Quiz Analytics

After a quiz session completes, analytics are available:

### Session Summary

| Metric             | Description                         |
| ------------------ | ----------------------------------- |
| Total Students     | Number of participants              |
| Average Score      | Mean score across all students      |
| Highest Score      | Best individual score               |
| Completion Rate    | Percentage who answered all questions |
| Average Response Time | Mean time per question            |

### Per-Question Analysis

- Response distribution chart
- Correct answer percentage
- Most common incorrect answer
- Time-to-answer distribution

### Student Leaderboard

- Ranked list of students by score
- Individual question-by-question breakdown
- Response time for each answer

---

## Troubleshooting

| Issue                          | Solution                                         |
| ------------------------------ | ------------------------------------------------ |
| Receiver not detected          | Check USB connection; try a different USB port    |
| Remote not pairing             | Press and hold the pairing button; check battery  |
| Student response not received  | Verify student mapping; check remote battery      |
| Slow response collection       | Ensure the USB receiver is within range            |
| Duplicate responses            | System deduplicates by MAC address per question   |

{% hint style="info" %}
Remote quizzes require the USB receiver hardware to be physically connected. For quizzes without hardware, use the **Web Quiz** feature instead.
{% endhint %}

---

## Next Steps

- [Test System](test-system.md) — Overview of all test types
- [Certificates](certificates.md) — Earn certificates on course completion
