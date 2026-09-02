# ACC 380K — Coding and Data Analysis in Accounting

**Fall 2026**<br>
**Unique numbers:** 03650, 03655, 37253

This syllabus is maintained in the course repository so that changes can be tracked over time. Canvas remains the authoritative source for current course requirements, deadlines, and policies.

## Instructor and Teaching Assistant

**Instructor:** Nicholas (Nick) Hallman — [nicholashallman@utexas.edu](mailto:nicholashallman@utexas.edu)<br>
**Office:** CBA 4M.228<br>
**Office hours:** Tuesday and Thursday, 3:30–5:00 p.m. [Book a 30-minute appointment](https://calendar.app.google/yuRCYe64PvvmBhSN6) at least two hours in advance; this is the preferred way to guarantee availability. Scheduled appointments take priority, but walk-ins are welcome when I am in the office and no scheduled appointment is in progress or about to begin. I usually expect to be there throughout the office-hours window, but if no appointments are booked, I may occasionally be away.

**Teaching Assistant:** Joanna G. Smith — [joanna.smith@utexas.edu](mailto:joanna.smith@utexas.edu)<br>
Joanna’s office hours are by appointment and can be booked directly on [Google Calendar](https://calendar.app.google/5a2iouwypKBxqXvM6). If none of the posted times work with your class schedule, feel free to reach out.<br>
In preparation for the exam on October 22nd, Joanna will be hosting open office hours on Wednesday, Oct 21 from 3:30–6:30pm in the CBA Atrium. No appointment will be needed.

## Course Meeting Details

**Unique 03650**

- Time - Tuesday and Thursday, 12:30pm – 1:45pm
- Location - GSB 3.128
- Modality - In person

**Uniques 03655 and 37253**

- Time - Tuesday and Thursday, 2:00pm – 3:15pm
- Location - GSB 3.128
- Modality - In person

## Course Materials and Platforms

No textbook is required, but budget up to $200 in total for software and AI tools. Buy nothing until instructed. Bring an internet-connected laptop. We will also use the following during the semester:

- **[Canvas](https://utexas.instructure.com/courses/1450201):** Canvas is the official hub for announcements, requirements, deadlines, submissions, feedback, and grades. Check it before class; if another platform conflicts, Canvas controls.
- **Google Colab:** Colab is our shared Python notebook environment; no local installation is required. Start with the free tier, but its limits vary. If later case work needs a paid plan, I will give advance notice and check for student or university access first.
- **Course data files:** Data will come through direct links. Some files require a Colab Secrets token, provided when needed. Do not share restricted files or put them in public repositories.
- **[GitHub](https://github.com/njhallman/acc380k-fall-2026):** The public course repo holds selected code and materials, including the [released notebook index](notebooks/README.md) and [quiz review archive](quiz-review/README.md); Case 2 teams will use private repos. No prior Git or GitHub experience, paid plan, or public student repo is required.
- **Claude Code and other AI tools:** We expect to use Claude Code and may use other AI tools, especially for the cases. Buy nothing now; I will give advance notice if paid access is necessary. The AI Policy below controls use.
- **Poll Everywhere:** Poll Everywhere supports ungraded in-class retrieval competitions; no account is required. Each question set is added to the quiz review archive after both sections have seen it.

## Course Description and Approach

### Course Focus

Despite the course title, this is primarily a coding and data-analysis course, not an accounting course in the usual sense. We will use Python to learn how computational workflows fit together, how to work with data, and how to decide whether an output is believable. Most skills are domain-agnostic. Some later applications use public-company, mobility, or SEC filing data. Our recurring habit will be: Read → Predict → Run → Assess → Test.

### Course AI Policy

In accordance with the University’s Institutional Rules on Student Services and Activities, Chapter 11, students accept the responsibility to always uphold academic integrity and an honor code reflective of a scholarly community devoted to academic and personal success. All members of the University community are fully accountable and responsible for any output they produce as part of academic work. In this course, generative AI use is partially permitted. It may be used on homework, Case 1, during Case 2 development, and on all other regular coursework. No disclosure is required for permitted AI use. Generative AI and other outside assistance may not be used during the in-person, pencil-and-paper midterm or the Case 2 interview. Any code or analysis you submit is yours to stand behind. You should be able to explain it, change it, identify how it could fail, and show how you tested the result.

## Course Learning Objectives

Homework, the in-person midterm, Case 1, Case 2, and the Case 2 interview assess the following outcomes. By the end of the course, you should be able to:

1. Read, trace, and explain Python code that uses variables, types, data structures, functions, conditionals, and loops.
2. Write and modify code in a notebook and explain how execution order, file paths, and stored state affect the result.
3. Use Pandas and related packages to load, clean, reshape, merge, analyze, and visualize data.
4. Identify a dataset’s grain—what one row represents—and describe its schema, including its columns, keys, and data types; assess missing values and duplicate records.
5. Diagnose joins by checking keys, cardinality, row counts, and unmatched observations.
6. Distinguish syntax and runtime errors from the more dangerous errors that run but produce a wrong result.
7. Test an analysis with known cases, reconciliations, assertions, and changed inputs.
8. Create and assess visualizations that support clear, appropriately limited claims.
9. Use GitHub and other course tools to preserve project history and document data sources and decisions so that teammates and other readers can reproduce and assess the work.
10. Explain and defend what an analysis does, why its result is credible, and where its limitations lie.

## Course Schedule and Assignments

![Fall 2026 course arc: foundations run August 25 through October 20; the midterm is October 22; Case 1 labs run October 27 through November 5; Case 2 labs run November 10 through November 19, with idea approval due November 12; the Case 2 showcase is December 1 and 3; interviews are December 10 or 12 by section. There is no class September 10 or November 24 and 26, and Joanna-supported sessions meet October 6 and 8 while Nicholas is away.](assets/acc380k-fall-2026-course-arc.png)

The figure above shows the expected broad progression of the course. In past semesters I have provided students with a class-meeting by class-meeting schedule of topics. We inevitably end up deviating from the schedule as the material gets covered more quickly or more slowly than I anticipate. So this year I am keeping things a little less detailed and a little more flexible. But the Course Learning Objectives section above should give you a sense of the material I hope to cover in the initial Aug-Oct phase of the course.

Homework will be assigned as we go and will not appear in this figure. Each homework assignment will be due one week after it is assigned. The assignment details and corresponding due date will be posted in Canvas. I anticipate approximately five homework assignments.

There will be one in-person, pencil-and-paper Midterm on Oct 22, 2026. It will assess your ability to read, trace, predict, debug, and explain pre-written Python code.

Case 1 is due Nov 5, 2026. Case 2 is due in stages. Every team must have an approved project idea by the end of class on Nov 12, 2026. Final Case 2 project files are due before class on Dec 1, 2026. The in-class Case 2 showcases will take place on Dec 1, 2026 and Dec 3, 2026. The Case 2 team interviews will occur either prior to finals week or during this course’s assigned finals period (Dec 10, 2026 or Dec 12, 2026 depending on section). Each team will receive an approximately 20-minute appointment; the interview is part of Case 2, not a separate cumulative final exam. Interviews will be scheduled through team sign-ups; exact appointment dates, times, and logistics will be posted in Canvas later in the semester.

## Assignments and Grading

Grades will be determined by homework assigned throughout the semester, an individual Case 1, a team-based Case 2, and an in-person midterm. Case 1 is a guided data-analysis and exploration assignment submitted as a Colab notebook; you will use cell-phone-derived foot-traffic and public-company data to build and assess a model that predicts sales. Case 2 is the deliberately open-ended “make something cool” project. Teams may choose a project that is interesting, valuable, or useful, and the deliverable need not be a notebook. Each team will maintain a private GitHub repository as its technical workspace and versioned project history; the required submission and grading record will remain in Canvas. The midterm is individual, in person, pencil and paper, and tests code reading, tracing, prediction, debugging, and explanation without AI or other outside tools.

| Component | Total Points |
|---|---:|
| Homework assigned throughout the semester | 25 |
| Case 1 | 20 |
| Case 2 - project, showcase, and interview | 30 |
| One in-person midterm exam | 25 |
| **Total** | **100** |

## Letter Grades

Letter grades will be assigned based on the number of points earned on the exams and assignments above. The table below presents the letter-grade floors. I reserve the right to curve letter grades up, but never down, from this standard.

| Points earned/points available | Letter Grade |
|---|:---:|
| Earned points ≥ 93 points | A |
| Earned points < 93 but ≥ 90 | A- |
| Earned points < 90 but ≥ 87 | B+ |
| Earned points < 87 but ≥ 83 | B |
| Earned points < 83 but ≥ 80 | B- |
| Earned points < 80 but ≥ 77 | C+ |
| Earned points < 77 but ≥ 73 | C |
| Earned points < 73 but ≥ 70 | C- |
| Earned points < 70 but ≥ 60 | D |
| Earned points < 60 | F |

## Attendance Policy

I hated attendance policies when I was a student, and I do not enforce a general attendance requirement now. Not enforcing one keeps me honest and forces me to make attending class worth your time. Much of this course happens through live coding, Poll Everywhere questions, debugging, and small-group work. These activities will prepare you for the midterm and cases, and some will be difficult to recreate later. Attendance is not recorded and does not directly affect the course grade. If you believe you can achieve the grade you want without attending class, you are welcome to try. But you probably can’t.

## Missed Work and Religious Accommodations

If an emergency, serious illness, university-sponsored activity, or other significant conflict affects your work, contact me as soon as you reasonably can. I will determine a fair make-up or extension case by case. Late work without prior communication may receive no credit. Religious and disability accommodations will be implemented consistent with UT policy.

Notify me as far in advance as possible if observing a religious holy day will require you to miss class or graded work, and complete the [Office of the Dean of Students religious-accommodations form](https://cm.maxient.com/reportingform.php?UTAustin=&layout_id=400). You will have a reasonable opportunity after the absence to complete missed work, consistent with UT policy.

## Academic Integrity and Collaboration

All allegations of academic misconduct will be referred to Student Conduct and Academic Integrity in the Office of the Dean of Students. A student found responsible may receive both a conduct sanction and a course-grade impact. Assignment instructions define permitted collaboration and outside assistance. If a boundary is unclear, ask before submitting.

## Other Important Information

### Disability and Access

Students with disabilities may request appropriate academic accommodations from Disability & Access (D&A).

### Title IX Reporting

I am a mandatory reporter and must promptly share information about possible prohibited conduct involving a UT student or employee with the Title IX Office. For confidential support without making a Title IX report, contact the Confidential Case Manager for Students at [advocate@austin.utexas.edu](mailto:advocate@austin.utexas.edu) or 512-232-2860. To report, request support, or seek pregnancy or parenting accommodations, visit [titleix.utexas.edu](https://titleix.utexas.edu/) or call 512-471-0419.

### Classroom Recording

HOP 2-9970 prohibits students from recording class instruction (audio or video) unless a student obtains the instructor’s permission or Disability & Access has approved audio recording as an accommodation.

### University Policies and Resources for Students

UT maintains a consolidated [University Policies and Resources for Students page in Canvas](https://utexas.instructure.com/enroll/TP964H) covering student services, safety, academic support, and other policies relevant to this course.
