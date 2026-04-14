# Test System

TinkerBunker provides a comprehensive test system with multiple test types for different educational scenarios — from embedded course assessments to standalone teacher tests and live remote quizzes.

---

## Test Types Overview

| Test Type        | Purpose                          | Created By      | Context                  |
| ---------------- | -------------------------------- | --------------- | ------------------------ |
| Pre-Test         | Assess knowledge before course   | Admin Creator   | Embedded in course       |
| Post-Test        | Evaluate learning after course   | Admin Creator   | Embedded in course       |
| Inline Test      | Periodic chapter assessment      | Admin Creator   | Embedded in chapter      |
| Teacher Test     | Standalone assessment            | Teacher         | Independent of courses   |
| Practice Test    | Self-paced practice              | Teacher         | Student-driven attempts  |
| Assigned Test    | Formal assignment with deadline  | Teacher         | Class-based assignment   |
| Remote Quiz      | Live quiz with physical remotes  | Teacher         | Real-time classroom      |
| Web Quiz         | Live quiz via web browser        | Teacher         | Real-time online         |

---

## Question Formats

All test types support the following question formats:

| Format        | Description                                      |
| ------------- | ------------------------------------------------ |
| `mcq`         | Multiple choice — single or multi-select answers |
| `descriptive` | Free-form text response                          |
| `code`        | Code-based answer with an integrated editor      |

---

{% tabs %}
{% tab title="Course Tests" %}
## Course Tests (Pre / Post / Inline)

Course tests are embedded directly within courses and are created by **Admin Creators** during the course creation process.

### Pre-Test

- Placed at the **beginning** of the course
- Assesses baseline knowledge before learning begins
- Results help measure learning gain when compared with the post-test
- Configured at the course level

**Setup:**
1. Open the course in edit mode
2. Navigate to course settings
3. Enable **Pre-Test**
4. Add questions with correct answers
5. Configure attempt limits

### Post-Test

- Placed at the **end** of the course
- Evaluates overall learning outcomes
- Scores contribute to the completion percentage
- Results factor into certificate generation

**Setup:**
1. Open the course in edit mode
2. Navigate to course settings
3. Enable **Post-Test**
4. Add questions with correct answers
5. Configure attempt limits

### Inline Test

- Embedded **within chapters** between content pages
- Tests understanding of recently covered material
- Has an `order` field to position it relative to pages
- Can be locked after maximum attempts

**Setup:**
1. Open a chapter
2. Click **Add Test** (content type: `test`)
3. Set the test order within the chapter
4. Add questions
5. Configure attempt limits and lock behavior

### Attempt Configuration

| Setting              | Description                                   |
| -------------------- | --------------------------------------------- |
| `default_max_attempts` | Maximum times a student can attempt the test |
| `is_locked`          | Lock the test after max attempts are reached  |

<figure><img src="../.gitbook/assets/course-test-config.png" alt="Course Test Configuration"><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Teacher Tests" %}
## Teacher Tests

Teacher tests are standalone assessments created by teachers, independent of any course. They are managed from the **Teacher Tests Dashboard**.

### Accessing the Dashboard

1. Log in as a **Teacher**
2. Navigate to **Tests** (`/teacher-tests`) from the sidebar
3. The dashboard shows two tabs: **Tests** and **Assignments**

### Creating a Teacher Test

1. Click **Create Test**
2. Fill in the test details:

| Field          | Required | Description                            |
| -------------- | -------- | -------------------------------------- |
| Title          | Yes      | Test name                              |
| Description    | No       | Test instructions and overview         |
| Subject        | Yes      | Subject area                           |
| Duration       | No       | Time limit in minutes                  |
| Total Marks    | Yes      | Maximum marks for the test             |

3. Add questions (MCQ, descriptive, or code)
4. Set correct answers and marks per question
5. Click **Save**

### Managing Tests

From the Tests tab:

| Action   | Description                              |
| -------- | ---------------------------------------- |
| View     | Preview the test and its questions       |
| Edit     | Modify questions, marks, or settings     |
| Delete   | Remove the test                          |
| Assign   | Create an assignment from this test      |

<figure><img src="../.gitbook/assets/teacher-tests-dashboard.png" alt="Teacher Tests Dashboard"><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Assigned Tests" %}
## Assigned Tests (Assignments)

Assignments connect teacher tests with classes, adding deadlines and evaluation workflows.

### Creating an Assignment

1. From the Teacher Tests Dashboard, select a test
2. Click **Create Assignment**
3. Configure the assignment:

| Field          | Required | Description                          |
| -------------- | -------- | ------------------------------------ |
| Class          | Yes      | Target classroom                     |
| Due Date       | Yes      | Submission deadline                  |
| Instructions   | No       | Additional instructions for students |

4. Click **Create** (assignment starts in `DRAFT` status)

### Assignment Lifecycle

```
DRAFT → PUBLISHED → COMPLETED
```

| Status      | Description                                     |
| ----------- | ----------------------------------------------- |
| `DRAFT`     | Assignment created but not visible to students  |
| `PUBLISHED` | Assignment is live and students can submit       |
| `COMPLETED` | Deadline passed or manually completed            |

### Publishing an Assignment

1. Open the draft assignment
2. Click **Publish**
3. Students in the assigned class receive the assignment

### Student Submissions

Students submit their answers through:
- Online form (MCQ and descriptive)
- PDF upload (for handwritten answers via `AsyncPDFUpload`)

### Evaluating Submissions

1. Navigate to **Assignments** tab
2. Click on the completed assignment
3. Open the **Evaluation Page**
4. Review each student's submission:

| Evaluation Feature       | Description                                    |
| ------------------------ | ---------------------------------------------- |
| Intent Scoring           | AI-assisted intent-based evaluation            |
| Manual Scoring           | Teacher manually assigns marks                 |
| Intent Configuration     | Configure evaluation criteria per question     |
| Combined PDF             | Generate a combined PDF of all submissions     |
| Finalization             | Lock scores and generate final results         |

### AI-Powered Evaluation

The platform supports AI-assisted evaluation with configurable models:

| Model    | Provider | Description                   |
| -------- | -------- | ----------------------------- |
| `openai` | OpenAI   | GPT-based evaluation          |
| `xai`    | xAI      | Alternative AI evaluation     |

Processing statuses:
```
IDLE → PENDING → PROCESSING → COMPLETED / FAILED
```

<figure><img src="../.gitbook/assets/assignment-evaluation.png" alt="Assignment Evaluation"><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Practice Tests" %}
## Practice Tests

Practice tests allow students to repeatedly practice assessments at their own pace with attempt tracking.

### How Practice Tests Work

1. Teacher creates a practice test (or it is generated from course content)
2. Students access the practice test from their course or dashboard
3. Students can attempt the test multiple times (within attempt limits)
4. Each attempt is tracked with scores

### Attempt Tracking

The system tracks remaining attempts using `getRemainingAttempts`:

| Metric             | Description                              |
| ------------------ | ---------------------------------------- |
| Total Attempts     | Maximum allowed attempts                 |
| Attempts Used      | Number of completed attempts             |
| Remaining Attempts | Total minus used                         |
| Best Score         | Highest score across all attempts        |

### Progress Tracking

Practice test progress is tracked for:
- **Teachers** — View class-wide practice test performance
- **Students** — Track personal progress and scores
- **Public users** — Track progress on public course practice tests

### Taking a Practice Test

1. Navigate to the course or test section
2. Click on the practice test
3. Answer all questions within the time limit (if set)
4. Submit the test
5. View immediate results and score
6. Retry if attempts remain
{% endtab %}

{% tab title="Remote Quiz" %}
## Remote Quiz

Remote quizzes use **physical USB receiver devices** to enable real-time, interactive classroom quizzes. See the dedicated [Remote Quiz](remote-quiz.md) documentation for full details.

### Quick Overview

- Teachers run live quiz sessions in the classroom
- Students respond using physical remote clickers
- Remotes communicate via USB receivers connected to the teacher's device
- Real-time response tracking and results display

### Flow

```
Receiver Selection → Student Mapping → Quiz Ready → Quiz Active →
Question Response → Question Results → Quiz Complete
```
{% endtab %}

{% tab title="Web Quiz" %}
## Web Quiz Sessions

Web quizzes provide an online alternative to remote quizzes, allowing students to participate via their web browsers.

### Features

- Real-time quiz participation via browser
- No physical hardware required
- Supports the same question types as remote quizzes
- Session management with active/completed/cancelled statuses

### Running a Web Quiz

1. Teacher creates a quiz session
2. Students join the session via their browsers
3. Questions are presented one at a time
4. Students submit answers in real-time
5. Teacher can view live response data
6. Session completes with analytics

### Quiz Session Statuses

| Status      | Description                         |
| ----------- | ----------------------------------- |
| `active`    | Quiz session is currently running   |
| `completed` | Quiz session has ended              |
| `cancelled` | Quiz session was cancelled          |

### Analytics

After completion, view the **Quiz Analytics Dashboard**:
- Per-question response distribution
- Student performance breakdown
- Time-to-answer metrics
- Session history for past quizzes
{% endtab %}
{% endtabs %}

---

## Test Screen Features

All test types share common test-taking features:

| Feature         | Description                                            |
| --------------- | ------------------------------------------------------ |
| Timer           | Countdown timer for timed tests                        |
| Question Nav    | Navigate between questions                             |
| Flag Questions  | Mark questions for later review                        |
| Auto-Save       | Answers are saved automatically                        |
| Submit          | Final submission with confirmation                     |
| Review Mode     | Review answers after submission (if enabled)           |

---

## Next Steps

- [Remote Quiz](remote-quiz.md) — Detailed remote quiz setup and usage
- [Certificates](certificates.md) — Earn certificates on course completion
- [Course Lifecycle](course-lifecycle.md) — How tests fit into the course structure
