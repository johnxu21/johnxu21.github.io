---
layout: page
title: CS 789 - Software Reengineering
permalink: /teaching/Software-Reengineering/
---
<form action="/teaching/Software-Reengineering/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>
<form action="/teaching/Software-Reengineering/metrics/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Metrics and Visualization" />
</form>
<form action="/teaching/Software-Reengineering/refactoring/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Refactoring Assistants" />
</form>
<form action="/teaching/Software-Reengineering/dynamic/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Dynamic Analysis: Testing" />
</form>
<form action="/teaching/Software-Reengineering/integration/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Software Integration" />
</form>
<form action="/teaching/Software-Reengineering/msr/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Mining Software Repositories" />
</form>
<form action="/teaching/Software-Reengineering/project/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Reengineering Project" />
</form>

<br/>
<br/>



* Level: Masters 
* Period: Fall Semester 2025

Where ? When ?
* Theory & Exercises all during the same time slot
* Time: MoWe 5:30PM-6:45PM
* Location: FDH 217

**Communication**

Office Hours Feel free to reach out for assistance! You can send me a DM on Discord for private communication or post your question in any relevant Discord channel for group discussions and support.
Discord workspace: [Discord](https://discord.gg/kqzZwSFv)


- **Credits**: 3
- **Prerequisites**: Graduate standing. Prior knowledge of data structures and advanced programming is expected.
- **[Introductory Slides](Introduction.pdf)**

Rationale
======
Modernizing and extending existing software systems is a critical challenge in software engineering. CS 789 – Software Reengineering focuses on techniques for analyzing, restructuring, and improving legacy systems to enhance maintainability and prepare them for new functionality. Students will apply reverse engineering, refactoring, software integration, dynamic analysis, and repository mining to transform existing software architectures. Through lectures, hands-on labs, and project-based learning, students gain practical experience with industry-standard tools, preparing them for careers in software maintenance, modernization, and system evolution.

Catalog Description:
=====
This course explains the 'state-of-the-art' changing an existing software systems. This includes an introduction 
to the recent research, as well as an overview of the principles techniques and skills applied in practice today. 
Students will acquire a range of principles, techniques, and skills that are currently being used for changing an
existing software systems. Consequently, the **course has a practical ring to it with a minimal theoretical content**
(taught as reengineering patterns), several lab-sessions (experimenting with a suite of reengineering tools) and
one project (extending an existing large software system).



Objectives (expected learning outcomes)
======
To goal of this course is to become acquainted with a broad selection of principles, techniques and skills used when changing existing software systems. After this course, a student will be able to:
* assess which parts should be reengineered first;
* identify the risks and opportunities for a given re-engineering project;
* extract coarse-grained and fine-grained design models;
* select the most appropriate integration strategy;
* exploit tests during program change;
* solve the typical problems of an object-oriented re-engineering project.

Time schedule
=======
To realize these objectives, the course is organized as follows. We start with an introductory class outlining 
the state of the art in re-engineering and proceed with a couple of lab sessions (marked with [L] in the detailed 
time-schedule), in which several reverse and re-engineering tools will be tested under lab conditions. 
Afterward, students will experiment with these tools and the associated techniques in realistic circumstances by 
means of a Project, which will also serve as the main outcome.

Milestones
====

* **Announce Project**: At the outset of the project, students should announce which software system they intend to reengineer (yes, you can propose one yourself) in groups (since we are 11 students, we will allow 3 groups of 3 and one group of 2).
* **Precondition Report - Project Setup**. When announcing the project, students should demonstrate that they meet the necessary pre-condition to start the project. They need to have a Git repository for their project and also show the ability to successfully build the project.
* **Intermediate Report - Tool Usage**: One third into the project, each group should hand in a status report containing screenshots of the tools applied on the project, and interpretations about these results.
* **Final Report**: During the exam period you hand in a final report, listing the solutions for the problems you came across and what you learned from them. You will defend this report orally.

Below is the detailed time-schedule, which is subject to change. Changes will be notified over e-mail. [Last modified on Aug, 22th, 2025.] 

<table style="border-collapse:collapse;">
<tr >
<th style="border: 1px solid black;">Week</th>
<th style="border: 1px solid black;">Date</th>
<th style="border: 1px solid black;">Class Topic</th>
<th style="border: 1px solid black;">Date</th>
<th style="border: 1px solid black;">Class Topic</th>
</tr>

<tr>
<td style="border: 1px solid black;">01</td>
<td style="border: 1px solid black;">Mo 08/25</td>
<td style="border: 1px solid black;">[T] Class overview</td>
<td style="border: 1px solid black;">We 08/27</td>
<td style="border: 1px solid black;">[T] Introduction </td>
</tr>

<tr>
<td style="border: 1px solid black;">02</td>
<td style="border: 1px solid black;">Mo 09/01</td>
<td style="border: 1px solid black;">Public Holiday </td>
<td style="border: 1px solid black;">We 09/03 </td>
<td style="border: 1px solid black;">[L] Metrics and Visualization </td>
</tr>

<tr>
<td style="border: 1px solid black;">03</td>
<td style="border: 1px solid black;">Mo 09/08 </td>
<td style="border: 1px solid black;">[L] Refactoring assistants 1</td>
<td style="border: 1px solid black;">We 09/10 </td>
<td style="border: 1px solid black;">[L] Refactoring assistants 2</td>
</tr>

<tr>
<td style="border: 1px solid black;">05</td>
<td style="border: 1px solid black;">Mo 09/15 </td>
<td style="border: 1px solid black;">[L] Dynamic Analysis: Testing 1 </td>
<td style="border: 1px solid black;">We 09/17 </td>
<td style="border: 1px solid black;">[L] Dynamic Analysis: Testing 2 </td>
</tr>

<tr>
<td style="border: 1px solid black;">04</td>
<td style="border: 1px solid black;">Mo 09/22</td>
<td style="border: 1px solid black;">[L] Software Integration  1 </td>
<td style="border: 1px solid black;">We 09/24 </td>
<td style="border: 1px solid black;">[L] Software Integration 2 </td>
</tr>




<tr>
<td style="border: 1px solid black;">06</td>
<td style="border: 1px solid black;">Mo 09/29</td>
<td style="border: 1px solid black;">[L] Mining Software Repositories  1 </td>
<td style="border: 1px solid black;">We 10/01</td>
<td style="border: 1px solid black;">[L] Mining Software Repositories 2</td>
</tr>


<tr>
<td style="border: 1px solid black;">07</td>
<td style="border: 1px solid black;">Mo 10/06</td>
<td style="border: 1px solid black;">Free project Work</td>
<td style="border: 1px solid black;">We 10/08</td>
<td style="border: 1px solid black;">Free project Work <br/> <b>[Milestone 0] Groups Assembled + <br/> Precondition report</b> </td>
</tr>

<tr>
<td style="border: 1px solid black;">08</td>
<td style="border: 1px solid black;">Mo 10/13</td>
<td style="border: 1px solid black;">Free project Work  </td>
<td style="border: 1px solid black;">We 10/15</td>
<td style="border: 1px solid black;">Free project Work</td>
</tr>

<tr>
<td style="border: 1px solid black;">09</td>
<td style="border: 1px solid black;">Mo 10/20 </td>
<td style="border: 1px solid black;">Free project Work </td>
<td style="border: 1px solid black;">We 10/22</td>
<td style="border: 1px solid black;">Free project Work <br> <b> [Milestone 1] Report on usage of tools</b></td>
</tr>

<tr>
<td style="border: 1px solid black;">10</td>
<td style="border: 1px solid black;">Mo 10/27</td> 
<td style="border: 1px solid black;">Free project Work <br/> <b>[Milestone 1] Feedback Session</b></td>
<td style="border: 1px solid black;">We 10/29</td>
<td style="border: 1px solid black;">Free project Work </td>
</tr>

<tr>
<td style="border: 1px solid black;">11</td>
<td style="border: 1px solid black;">Mo 11/03</td>
<td style="border: 1px solid black;">Free project Work </td>
<td style="border: 1px solid black;">We 11/05</td>
<td style="border: 1px solid black;">Free project Work <br> <b> [Milestone 2] Intermediate Report</b></td>
</tr>

<tr>
<td style="border: 1px solid black;">12</td>
<td style="border: 1px solid black;">Mo 11/10</td>
<td style="border: 1px solid black;">Free project Work</td>
<td style="border: 1px solid black;">We 11/12</td>
<td style="border: 1px solid black;">Free project Work </td>
</tr>

<tr>
<td style="border: 1px solid black;">13</td>
<td style="border: 1px solid black;">Mo 11/17</td>
<td style="border: 1px solid black;">Concluding Remarks <br> <b>[Milestone 2] Feedback session</b></td>
<td style="border: 1px solid black;">We 11/19</td>
<td style="border: 1px solid black;">Free project Work</td>
</tr>

<tr>
<td style="border: 1px solid black;">14</td>
<td style="border: 1px solid black;">Mo 11/24</td>
<td style="border: 1px solid black;">Free project Work</td>
<td style="border: 1px solid black;">We 11/26</td>
<td style="border: 1px solid black;">Free project Work</td>
</tr>

<tr>
<td style="border: 1px solid black;">15</td>
<td style="border: 1px solid black;">Mo 12/01</td>
<td style="border: 1px solid black;">Free project Work</td>
<td style="border: 1px solid black;">We 12/03</td>
<td style="border: 1px solid black;">Free project Work >> <b>Final Report</b></td>
</tr>

<tr>
<td style="border: 1px solid black;">16</td>
<td style="border: 1px solid black;">Mo 12/08</td>
<td style="border: 1px solid black;"></td>
<td style="border: 1px solid black;">We 12/10</td>
<td style="border: 1px solid black;"><b> Exam</b></td>
</tr>

</table>

<br/>
<br/>

Course Material
=======
All students should have read the following book; acquiring the terminology inside is required to write the final project report.
* [Serge Demeyer, Stephane Ducasse, and Oscar Nierstrasz. Object-Oriented Reengineering Patterns. Morgan Kaufmann, 2002.](http://scg.unibe.ch/download/oorp/)
  * The original edition is available in the library of the University of Antwerp. It was published by Morgan Kaufmann in 2003, and is now out-of-print. 
* Alternatively, there is a publicly available PDF ([under the Creative Commons Attribution-ShareAlike 3.0 license](https://creativecommons.org/licenses/by-sa/3.0/))

For the lab sessions there is the following material (please only get the materials after it is updated to the current year):

1. [Metrics and Visualization](/teaching/Software-Reengineering/metrics/) (Updated 2025-08-16)
2. [Refactoring assistants](/teaching/Software-Reengineering/refactoring/) (Updated 2025-08-16)
3. [Dynamic Analysis: Testing](/teaching/Software-Reengineering/dynamic/) (Updated 2025-08-16)
4. [Software Integration](/teaching/Software-Reengineering/integration/) (Updated 2025-08-16)
5. [Mining Software Repositories](/teaching/Software-Reengineering/msr/) (Updated 2024-08-16)

Project
======

To demonstrate that you indeed acquired the range of principles, techniques, and skills that are currently being 
used for changing a project students must restructure an existing software system to prepare for a given suite of 
new requirements. Note, that the extra functionality as such needs not be implemented; but that the existing 
design must be adjusted in such a way that adding the new functionality becomes a proverbial "piece of cake".

Project: Assignment 
===============

**Milestones**
All Deliverables will be submitted on Canvas
* Monday 12-Oct-2025 - 11h59 pm - Project Definition & Group Assembly & Precondition Report: Confirm your project and group members on Canvas. Include a precondition report, details of this report to follow on the [project page]().
* Wednesday 26-Oct-2025 - 11h59 pm - Intermediate Report - Tool Usage: Send the Intermediate Report (in PDF format).
* Wednesday 16-Nov-2025 Concluding Session & Feedback Session
* Wednesday 30-Nov-2025 11h59pm (**Date to be confirmed**; one week before the oral exam) - Final Report: Send the Report (in PDF format).
* The oral exams (**Tobe confirmed**)

Group Work
========
It is possible (even encouraged) to work out the assignment in a group, but such a group will preferably not 
consist of more than three individuals. Of course, the expectations towards the end result of such a project 
are related to the size of the group. Also, remember that all members of the group will be given the same 
grade (report-wise).

Exam
========
The end result of this project consists of a written project report that needs to be elaborated upon during 
an oral project defense. Emphasis is on the solutions for the problems you came across and what you learned 
from them. Everything you claim in your project report must be backed up during the defense, using code and 
electronic documentation. The actual exam (= oral defense) takes place during the regular exam period and is 
scheduled accordingly. The report needs to be handed in a week beforehand electronically.

Guidelines for the Intermediate Report - Tool Usage
========
This report should be concise and to the point; its main purpose is to demonstrate that you have had personal 
hands-on experience with the tool suite explored in the lab sessions.

For each tool

* show at least one screen-dump with the results of applying the tool on the project
* provide brief interpretations (telegram style) of what you observe and what actions you would consider
* give estimations on when your tasks will be completed

Guidelines for the Final Report
============
* Short summary (Who, What, How): Who are the target users? What was the problem? How did we go about things?
* Status: What did you do, and what is (possibly) going to happen next?
* Which techniques and reengineering patterns did you use during requirements analysis, design, implementation, testing, and integration. How did you identify the differences between the old requirements and the new ones, the old design and the new one? How did you transform the existing code into the new code? How did you ensure these restructurings did not introduce any errors?
* Project process: Overview of planning, time schedule, and intermediary problems.

In the project report and during the project defense you should express yourself using the right terminology. (cfr . [Serge Demeyer, Stephane Ducasse, and Oscar Nierstrasz. Object-Oriented Reengineering Patterns. Morgan Kaufmann, 2002](http://scg.unibe.ch/download/oorp/)).

Evaluation Criteria
============

A. PRECONDITIONS: You have to meet the following entry criteria; if you don't your project report will be discarded without evaluation
 * You have submitted the Intermediate Report on Tool Usage on time
 * You did not copy other students work (we do check for plagiarism)

B.  SELECTION: In order to receive a passing grade (MINIMUM NORM), you have to show that you are at least capable of restructuring an existing software system.
 * You can extract the existing design from the available data (i.e. reverse engineering)
 * You can transform the existing source code so that it is more fit to implement the new requirements (i.e. refactoring)
 * You can demonstrate that the code transformations have not affected the existing functionality (i.e. regression tests)
 
C. DIVERSIFICATION: To do better than a passing grade, you have to show that you have control over the restructuring process.
 * Which techniques (re-engineering patterns) did you use for the different phases? To what extent are you able to back up your choice?
 * How did you analyze the new requirements? To what extent will you be able to maintain control over future changing requirements?
 * How did you validate the design (architecture) that you extracted from the source code? How did you use this design to identify potential problems?
 * How did you handle the code transformation itself? Why will these transformations help to implement the new functionality which is to be added?
 * How did you check on the quality of your test procedure? To what extent are you able to justify the amount of time you put into the testing, related to the existing functionality and the improvements that were made?
 * How did you handle the restructuring process itself? How accurate were your planning and estimation? How did you react to unanticipated circumstances?

The following check-list will be used to assess your reengineering project
* Checklist reengineering Pre-conditions Report [ PDF ](../../files/spdd/Pre-conditions_Report_Evaluation_Template.pdf)
* Checklist reengineering Intermediate Report [ PDF ](../../files/spdd/Intermetdiate_Evaluation_Report_Template.pdf)
* Checklist reengineering Final Report [PDF](../../files/spdd/Final_Report_Evaluation_Form_Blank.pdf)

--------
**Table I: Grade Distribution:**

<div style="text-align: center;">
<img src="/files/grade.jpeg" alt="Grade Distribution" style="width:577px;height:414px;" align="center">
</div>

## Attendance:	
While I will not directly track your attendance, your class, even online, is designed to be interactive with your classmates. The purpose of this is to encourage active learning, where you engage with the material during the class sessions. As such, a video would not do the course justice and you are highly recommended to attend the online sessions.

## Academic Misconduct
Academic integrity is a legitimate concern for every member of the campus community; all share in upholding the fundamental values of honesty, trust, respect, fairness, responsibility and professionalism. By choosing to join the UNLV community, students accept the expectations of the Student Academic Misconduct Policy and are encouraged when faced with choices to always take the ethical path. Students enrolling in UNLV assume the obligation to conduct themselves in a manner compatible with UNLV's function as an educational institution. Many of us on the computer science faculty share, or copy, very similar statements about misconduct.
An example of academic misconduct is plagiarism. Plagiarism is using the words or ideas of another, from the Internet or any source, without proper citation of the sources. See the Student Academic Misconduct Policy (approved December 9, 2005) located at: http://studentconduct.unlv.edu/misconduct/policy.html

## Department of Computer Science Academic Integrity Policy
Each student enrolled in a course offered by the Department of Computer Science is expected to do his/her own work when preparing written or programming assignments, as well as, examinations. He/She must adhere to the academic integrity policy provided by his/her instructor and the university. It is also each student's responsibility to notify the instructor if he/she becomes aware of any activities that would violate the academic integrity policy of the class. I reserve the right to fail any student, from the assignment or the course, for violating the policy, at my discretion.

## Copyright
The University requires all members of the University Community to familiarize themselves with and to follow copyright and fair use requirements. You are individually and solely responsible for violations of copyright and fair use laws. The university will neither protect nor defend you nor assume any responsibility for employee or student violations of fair use laws. Violations of copyright laws could subject you to federal and state civil penalties and criminal liability, as well as disciplinary action under University policies. Additional information can be found at: www.unlv.edu/provost/copyright

## ADA Statement:
Students who have special needs or disabilities that may affect their ability to access information and/or material presented in this course are encouraged to contact me or appropriate on campus entities for additional disability-related educational accommodations. Also, excellent students with a documented disability are sometimes eligible for internship opportunities through a grant program out of the University of Washington. Those students that are interested may optionally get in touch with me about this if they wish. 

## Disability Resource Center (DRC)
The UNLV Disability Resource Center (SSC-A 143, http://drc.unlv.edu/, 702-895- 0866) provides resources for students with disabilities. If you feel that you have a disability, please make an appointment with a Disabilities Specialist at the DRC to discuss what options may be available to you. If you are registered with the UNLV Disability Resource Center, bring your Academic Accommodation Plan from the DRC to the instructor during o ce hours so that you may work together to develop strategies for implementing the accommodations to meet both your needs and the requirements of the course. Any information you provide is private and will be treated as such. If you desire to maintain the confidentiality of your request, please do not approach the instructor before or after class to discuss your accommodation needs.

## Incomplete Grades
The grade of I - Incomplete - can be granted when a student has satisfactorily completed three-fourths of course work for that semester/session but for reason(s) beyond the student's control, and acceptable to the instructor and the Department, cannot complete the last part of the course, and the instructor believes that the student can finish the course without repeating it. The incomplete work must be made up before the end of the following regular semester. If course requirements are not completed within the time indicated, a grade of F will be recorded and the GPA will be adjusted accordingly. Students who are fulfilling an Incomplete do not register for the course but make individual arrangements with the instructor who assigned the I grade.

## Tutoring
The Academic Success Center (ASC) provides tutoring and academic assistance for all UNLV students taking UNLV courses. Students are encouraged to stop by the ASC to learn more about subjects offered, tutoring times and other academic resources. The ASC is located across from the Student Services Complex (SSC). Students may learn more about tutoring services by calling 702-895-3177 or visiting the tutoring web site at:
http://academicsuccess.unlv.edu/tutoring/

## UNLV Writing Center
One-on-one or small group assistance with writing is available free of charge to UNLV students at the Writing Center, located in CDC-3-301. Although walk-in consultations are sometimes available, students with appointments will receive priority assistance. Appointments may be made in person or by calling 702-895- 3908. The student's Rebel ID Card, a copy of the assignment (if possible), and two copies of any writing to be reviewed are requested for the consultation. More information can be found at: http://writingcenter.unlv.edu/

## UNLV Library Resources
Students may consult https://www.library.unlv.edu/consultation with a librarian on research needs. For this class, the subject librarian is Sue Wainscott. See: https://www.library.unlv.edu/contact/librarians_by_subject for more information. UNLV Libraries provides resources to support students’ access to information. Discovery, access, and use of information are vital skills for academic work and for successful post-college life. Access library resources and ask questions at https://www.library.unlv.edu.

## Rebelmail
By policy, faculty and staff should e-mail students' Rebelmail accounts only. Rebelmail is UNLV's official e-mail system for students. It is one of the primary ways students receive official university communication such as information about deadlines, major campus events, and announcements. All UNLV students receive a Rebelmail account after they have been admitted to the university. Students' e-mail prefixes are listed on class rosters. The suffix is always @unlv.nevada.edu. Emailing within WebCampus is acceptable.
Final Examinations
The University requires that final exams given at the end of a course occur at the time and on the day specified in the final exam schedule. See the schedule at:
http://www.unlv.edu/registrar/calendars.

## Caveat:
The schedule and procedures for this course are subject to change. It is the student's responsibility to learn of and adjust to changes.

## COVID-19:
COVID-19 has caused serious problems for all of us, students and faculty alike. It is possible that any of us this semester will have even more serious health or life challenges. Please keep this in mind when interacting with team mates, faculty, and others. A little bit of kindness and understanding goes a long way.




