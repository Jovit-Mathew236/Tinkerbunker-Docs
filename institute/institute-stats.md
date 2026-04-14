---
description: Institute-level analytics covering student performance, course adoption, and classroom activity.
---

# Institute Stats

The Institute Stats section provides a comprehensive view of your institute's performance. Use these analytics to identify trends, track course adoption, and monitor student engagement.

---

## Accessing Institute Stats

1. Navigate to **Dashboard → Institute Stats**.
2. The stats page loads with default filters (current academic term, all classrooms).

<figure><img src="../.gitbook/assets/institute-stats-overview.png" alt="Institute Stats Overview"><figcaption><p>Institute Stats — high-level performance summary</p></figcaption></figure>

---

## Summary Metrics

The top of the stats page displays key metrics:

| Metric                     | Description                                                |
| -------------------------- | ---------------------------------------------------------- |
| **Total Enrolled Students** | Students with approved status across all classrooms.       |
| **Active Students**         | Students who logged in within the last 7 days.             |
| **Total Classrooms**        | Number of classrooms currently in the institute.           |
| **Courses in Use**          | Number of distinct courses linked to at least one classroom. |
| **Average Completion Rate** | Mean course completion percentage across all students.     |

---

## Student Performance

The **Student Performance** panel provides:

- **Score Distribution** — histogram of student scores across all assessments.
- **Top Performers** — list of students with the highest average scores.
- **At-Risk Students** — students with completion rates below a configurable threshold (default: 30%).

{% hint style="info" %}
Use the at-risk student list to proactively reach out to students who may need additional support.
{% endhint %}

### Filtering by Classroom

You can filter student performance data by specific classrooms:

1. Use the **Classroom** dropdown at the top of the panel.
2. Select one or more classrooms.
3. The data refreshes to show only students in the selected classrooms.

---

## Course Adoption

The **Course Adoption** panel shows how effectively courses are being utilized:

| Column               | Description                                              |
| -------------------- | -------------------------------------------------------- |
| **Course Name**      | Name of the course.                                      |
| **Classrooms**       | Number of classrooms the course is linked to.            |
| **Students Enrolled**| Total students with access via linked classrooms.        |
| **Started (%)**      | Percentage of students who have opened at least one module. |
| **Completed (%)**    | Percentage of students who have completed all modules.   |

{% hint style="warning" %}
Low adoption rates may indicate that a course is not properly linked to classrooms or that students are unaware of the available content. Verify classroom-course links if adoption seems unusually low.
{% endhint %}

---

## Classroom Activity

The **Classroom Activity** panel provides a per-classroom breakdown:

- **Active vs. Inactive Classrooms** — classrooms with recent student activity versus those with none.
- **Average Logins per Classroom** — mean student login count over the selected time period.
- **Assignments Completed** — number of assignments submitted per classroom.

---

## Exporting Reports

You can export stats data for offline analysis:

1. Click the **Export** button at the top right of the stats page.
2. Select the format:
   - **CSV** — raw data suitable for spreadsheet tools.
   - **PDF** — formatted report with charts.
3. Choose the date range and filters to include.
4. Click **Download**.

{% hint style="info" %}
Exported reports respect the currently applied filters. Adjust filters before exporting to get the exact data set you need.
{% endhint %}

---

## Related

- [Dashboard](dashboard.md)
- [Managing Courses](managing-courses.md)
- [Managing Classrooms](managing-classrooms.md)
