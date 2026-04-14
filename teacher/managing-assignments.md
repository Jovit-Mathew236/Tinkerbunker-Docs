# Managing Assignments

Assignments connect your tests to students. You can assign tests to individual students or entire classrooms, set deadlines, track submissions, evaluate answers, and assign grades.

---

## Creating an Assignment

{% tabs %}
{% tab title="From the Tests Page" %}
1. Navigate to **Tests** in the navigation bar.
2. Find the test you want to assign.
3. Click the **Assign** button on the test card or detail page.
4. The assignment creation form opens.
{% endtab %}

{% tab title="From a Classroom" %}
1. Navigate to **Classroom** and open the classroom.
2. Go to the **Assignments** tab.
3. Click **Create Assignment**.
4. Select the test to assign from your test library.
{% endtab %}
{% endtabs %}

---

## Assignment Configuration

| Setting | Description | Required |
| ---------------------- | ------------------------------------------------------------------- | -------- |
| **Test** | The test to assign. Pre-filled if initiated from a test page. | Yes |
| **Assign To** | Select individual students, a classroom, or multiple classrooms. | Yes |
| **Due Date** | Deadline for the assignment. Students cannot submit after this date. | No |
| **Instructions** | Additional instructions or notes visible to students. | No |
| **Show Results After** | Whether students see results immediately or after your evaluation. | No |

{% hint style="info" %}
Assigning to a classroom automatically includes all current students in that classroom. Students added to the classroom later will also receive the assignment.
{% endhint %}

---

## Assignment Targets

| Target | Description |
| ---------------------- | ------------------------------------------------------------------- |
| **Individual Students**| Hand-pick specific students to receive the assignment. |
| **Classroom** | All students in the selected classroom receive the assignment. |
| **Multiple Classrooms**| Assign the same test across several classrooms simultaneously. |

---

## Tracking Submissions

Once an assignment is live, you can track student progress from the assignment detail page.

| Status | Meaning |
| ---------------- | -------------------------------------------------------------- |
| **Not Started** | The student has not opened the test yet. |
| **In Progress** | The student has started but not submitted the test. |
| **Submitted** | The student has completed and submitted the test. |
| **Evaluated** | You have reviewed and graded the submission. |

<figure><img src="../.gitbook/assets/assignment-tracking.png" alt="Assignment Tracking"><figcaption></figcaption></figure>

{% hint style="warning" %}
If a test has a time limit, students who start the test but do not submit within the time will have their test auto-submitted.
{% endhint %}

---

## Evaluation Workflow

After students submit their tests, you evaluate and grade them.

{% tabs %}
{% tab title="Auto-Graded Questions" %}
Questions with definitive answers (Multiple Choice, True/False, Fill in the Blank) are graded automatically.

- Correct answers receive full marks.
- Incorrect answers receive zero marks.
- You can override auto-graded scores if needed.
{% endtab %}

{% tab title="Manual Evaluation" %}
Subjective/Descriptive questions require manual evaluation:

1. Open the assignment detail page.
2. Click on a student's submission.
3. Review each subjective answer.
4. Enter the marks awarded for each question.
5. Optionally add feedback comments.
6. Click **Save Evaluation**.
{% endtab %}
{% endtabs %}

---

## Grading

| Grade Action | Description |
| ----------------------- | ---------------------------------------------------------------- |
| **View Submission** | Open a student's full test submission. |
| **Award Marks** | Enter marks for each manually graded question. |
| **Add Feedback** | Write comments on individual answers or overall feedback. |
| **Override Score** | Change the auto-graded score for a question if needed. |
| **Finalize Grade** | Mark the evaluation as complete and release results to student. |

{% hint style="info" %}
Students will not see their grades for manually evaluated questions until you finalize the evaluation.
{% endhint %}

---

## Evaluation Summary

The assignment page shows an aggregate summary:

| Metric | Description |
| ---------------------- | -------------------------------------------------------- |
| **Total Students** | Number of students assigned. |
| **Submitted** | Number of submissions received. |
| **Evaluated** | Number of submissions you have graded. |
| **Average Score** | Mean score across all evaluated submissions. |
| **Highest Score** | Top score in the class. |
| **Lowest Score** | Lowest score in the class. |

---

## Assignment Lifecycle

```
Created → Assigned → Students Take Test → Submitted → Evaluated → Grades Released
```

1. **Created** — You select a test and configure the assignment.
2. **Assigned** — Students receive the assignment and it appears on their dashboard.
3. **Students Take Test** — Students open and complete the test within the deadline.
4. **Submitted** — Answers are recorded and ready for review.
5. **Evaluated** — You review, grade, and finalize scores.
6. **Grades Released** — Students can see their scores and feedback.

{% hint style="warning" %}
Ensure you complete evaluations promptly. Students may be waiting for their results, especially if results are configured to show only after teacher evaluation.
{% endhint %}
