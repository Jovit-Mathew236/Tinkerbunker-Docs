# Creating Tests

TinkerBunker provides a powerful test creation tool that lets teachers build standalone tests from scratch. Tests can then be assigned to students, used as practice material, or deployed in live remote quiz sessions.

---

## Accessing Test Creation

1. Click **Tests** in the navigation bar.
2. Click the **Create Test** button.
3. The test creation form opens.

![Create Test](.gitbook/assets/create-test.png)

---

## Test Configuration

When creating a test, you configure several settings before adding questions.

| Setting | Description | Required |
| ---------------------- | ------------------------------------------------------------------ | -------- |
| **Title** | A descriptive name for the test. | Yes |
| **Description** | Optional overview of what the test covers. | No |
| **Duration** | Time limit in minutes. Leave empty for untimed tests. | No |
| **Total Marks** | Maximum marks for the test. Auto-calculated if not set manually. | No |
| **Shuffle Questions** | Randomize question order for each student. | No |
| **Show Results** | Whether students can see results immediately after submission. | No |

{% hint style="info" %}
Configuring a time limit is recommended for formal assessments. Practice tests can be left untimed to give students flexibility.
{% endhint %}

---

## Adding Questions

After configuring the test, add questions one by one.

### Question Types

| Type | Description |
| ------------------------------- | ------------------------------------------------------------------- |
| **Multiple Choice (Single)** | One correct answer from several options. |
| **Multiple Choice (Multiple)** | Multiple correct answers from several options. |
| **True / False** | A binary choice question. |
| **Fill in the Blank** | Students type a short answer. |
| **Subjective / Descriptive** | Open-ended answer requiring manual evaluation by the teacher. |

### Creating a Question

{% tabs %}
{% tab title="Multiple Choice" %}
1. Click **Add Question**.
2. Select **Multiple Choice** as the question type.
3. Enter the question text.
4. Add answer options (minimum 2, recommended 4).
5. Mark the correct answer(s).
6. Set the marks for this question.
7. Optionally add an explanation that students see after submission.
8. Click **Save Question**.
{% endtab %}

{% tab title="True / False" %}
1. Click **Add Question**.
2. Select **True / False**.
3. Enter the question statement.
4. Select whether the correct answer is True or False.
5. Set the marks.
6. Click **Save Question**.
{% endtab %}

{% tab title="Fill in the Blank" %}
1. Click **Add Question**.
2. Select **Fill in the Blank**.
3. Enter the question with a blank indicator.
4. Enter the accepted correct answer(s).
5. Set the marks.
6. Click **Save Question**.
{% endtab %}

{% tab title="Subjective" %}
1. Click **Add Question**.
2. Select **Subjective / Descriptive**.
3. Enter the question text.
4. Optionally provide a model answer for your own reference during evaluation.
5. Set the marks.
6. Click **Save Question**.
{% endtab %}
{% endtabs %}

---

## Editing a Test

You can edit an existing test at any time, provided it has not been submitted by students in an active assignment.

1. Navigate to **Tests** in the navigation bar.
2. Find the test in your test list.
3. Click the **Edit** button.
4. Modify the test settings or questions as needed.
5. Click **Save** to apply changes.

{% hint style="warning" %}
Editing a test that is part of an active assignment may affect students who have not yet started the test. Students who have already submitted will not be affected by changes.
{% endhint %}

---

## Managing Questions

Within the test editor, you can manage questions with the following actions:

| Action | Description |
| -------------- | --------------------------------------------------------------- |
| **Reorder** | Drag and drop questions to change their order. |
| **Edit** | Click on a question to modify its text, options, or marks. |
| **Delete** | Remove a question from the test. |
| **Duplicate** | Create a copy of an existing question for quick variations. |

---

## Test Preview

Before assigning a test, use the **Preview** feature to see how students will experience it.

1. Click the **Preview** button on the test detail page.
2. The test opens in a simulated student view.
3. Navigate through questions, test the timer, and verify the layout.
4. Close the preview to return to the editor.

{% hint style="info" %}
Always preview your test before assigning it. This helps catch formatting issues, incorrect answer keys, or missing questions.
{% endhint %}

---

## After Creating a Test

Once your test is ready, you can:

- **Assign it** to students or classrooms (see [Managing Assignments](managing-assignments.md)).
- **Use it in a Remote Quiz** (see [Remote Quiz](remote-quiz.md)).
- **Share it** as a practice test for self-paced student use.
