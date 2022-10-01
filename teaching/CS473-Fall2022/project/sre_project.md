---
layout: page
title: Reengineering Project - linkedin/kafka
permalink: /teaching/CS473-Fall2022/project/
---

<form action="/teaching/CS473-Fall2022/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>
<form action="/teaching/CS473-Fall2022/metrics/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Metrics and Visualization" />
</form>
<form action="/teaching/CS473-Fall2022/refactoring/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Refactoring Assistants" />
</form>
<form action="/teaching/CS473-Fall2022/integration/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Software Integration" />
</form>
<form action="/teaching/CS473-Fall2022/dynamic/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Dynamic Analysis: Testing" />
</form>
<form action="/teaching/CS473-Fall2022/msr/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Mining Software Repositories" />
</form>
<form action="/teaching/CS473-Fall2022/project/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Reengineering Project" />
</form>

<br/>
<br/>

Target Application
==============
[LinkedIn](https://github.com/linkedin/kafka) project is a variant fork of [Apache Kafka](https://github.com/apache/kafka) running at LinkedIn. 

Kafka was born at LinkedIn. The run thousands of brokers to deliver trillions of messages per day. They run a slightly modified version of Apache Kafka trunk. The [LinkedIn](https://github.com/linkedin/kafka) variant contains the LinkedIn Kafka release.

Assignment
==========

### 1. Contextualization of the Project

LinkedIn is a clone-and-own variant of Apache Kafka that was created by copying and adapting the existing 
code of Apache Kafka that was forked on 2011-08-15T18:06:16Z. The two software systems kept on synchronizing 
their new updates until 2022-02-22T13:32:39Z. Since 2022-02-22T13:32:39Z (divergence date), the two 
projects do not share common commits yet actively evolve in parallel. Currently (2022-02-28T15:01:39Z), 
LinkedIn has 500 individual commits, and Apache Kafka has 3,103 individual commits. Development becomes 
redundant with the continued divergence, and maintenance efforts rapidly grow. For example, if a bug is 
discovered in a shared file and fixed in one variant, it is not easy to tell if it has been fixed in the 
other variant.

### 2. Getting Started Instructions
Please pay attention to the following instructions. You need to send an email to <em></em><a href="mailto:john.businge@unlv.edu">me</a> with:
* Subject "Reengineering - Linkedin". 
* Message Body:
  * The full name of the members in your group (including yours). Remember, a maximum of 3 
  people, but you are allowed to work with less than 3 if you want to.
  * Attach the **pre-conditions report** (PDF format) in your message.

* Your Pre-conditions Report should contain the following:
  * Project Name
  * Full names of all the members in your group
  * A link to your GitHub repositories (which shows you already forked [LinkedIn])
  * A link to
  * The members are set as collaborators to the GitHub project.
  * Invite me as collaborator (my [GitHub ID - ```johnxu21```](https://github.com/johnxu21)).
* Demonstrate the ability to build the projects. For this, we want a statement from the group 
attesting they managed to successfully build the project. You can also attach a screenshot of 
your IDE with the project source and a message like "build successful".
* Simple Class Diagram of the class being patched (or buggy class). A simple class diagram has 
only the name of the class and its interactions with the other classes (there are two examples in 
JPacman repository in the "docs" folder). This is to reinforce your initial understanding of the 
system. You only need to focus on the classes associated with the patch and the classes that are 
called in those classes. There is no need to go deeper into the class structure (i.e., if buggy 
class calls Class X, and Class X calls Class Y, then you do not need to show Class Y since it is 
not being called directly by the buggy class). We are not going to evaluate your strictness to the 
proper UML notations, therefore focus on modeling and understanding classes interactions. 
* [Optional] A rough planning of the scope and goals. As you noticed the project refactoring is 
open to interpretation (this is on purpose). Therefore, is up to you, students, to plan the scope 
for your project. It is entirely possible for different groups to have different scopes and planned 
activities based on this assignment.

### 3. General Coding Instructions
In order to work on this assignment, the following coding/repository instructions apply:
* Fork [LinkedIn](https://github.com/linkedin/kafka), and clone the source code for your 
team to work on it. In the Documentation 
webpage, you can find further instructions on how to build the software (adapt accordingly, 
as many open source projects are a bit careless with keeping their documentation up-to-date).
* If you are working on this assignment as a group, then all members should be added to 
the repository as collaborators. 
* Commit/push your changes regularly providing information on the activity performed. 
Any "single" activity that requires file maintenance must be committed as a single commit 
with a simple description of the maintenance performed. For example, if you change the system 
to remove a God Class, your commit should be:
  * ```fixing merge conflicts on patch X, class Y  or unit tests for class Y.```
  * Another example, let's suppose you also introduced new ```tests``` along with the ```refactoring/code changes```:
  * ```refactoring Class Y to add the patch + new test added```
  * Of course, pushing the ```tests``` on a separate commit would also be acceptable (actually, it would be better to do so).
  * It is not considered good practice to commit a big chunk of modified files without providing a 
  reason that explains why those files have been modified. Therefore, try to split your commits 
  into smaller units (that may help with the grading).
  * Your GitHub commits history will be evaluated. Therefore, be sure to commit and push regularly.
  * Be sure to commit/push the final version of your reengineering project before the final 
  deadline. The final commit will be considered for evaluation as part of your assignment submission.

### 4. Development Activities 
Then, more specifically, we ask you to perform the following activities, and report about these in your project report:

----------
  [I. Design recovery]

<img src="/images/473/design_recovery.jpeg" alt="Design Recover" style="width:1263px;height:1080px;" align="center">

  1. Describe the current design implementation of the selected feature in the current Software. Clearly indicate how this design is located in the architecture of the project.

----------
  [II. Redesign]

<img src="/images/473/Redesign.jpeg" alt="Redesign" style="width:384px;height:131px;" align="center">

  2. Compose a generic design that describes how the new functionality / feature should be integrated 
and how the design handles the interaction with the rest of the system. It should be clear 
that the new design not only supports the new feature but also does not severely impact the 
code quality.
  
   It will be necessary to redesign the test suite in such a way that it can cope with the new feature and design.

----------
  [III. Management]

<img src="/images/473/project-management.jpeg" alt="Project Management" style="width:1024px;height:512px;" align="center">

  3. Estimate the effort required for (i) refactoring towards the new requirements; and (ii) changing/extending the tests.
--------
  [IV. Refactoring/ Code Change]

<img src="/images/473/refactoring.jpeg" alt="Project Management" style="width:300px;height:168px;" align="center">

  4. Refactor the current implementation of the Software such that it can handle the new feature.

   Adjust/extend the tests of the project to preserve their effectiveness and coverage during and after refactoring.

----------

* You will be required to perform a number of techniques presented during the lab sessions. These are:
  * Analyzing: Metrics and Visualization; and Mining Software Repositories.
  * Restructuring: Testing; and Refactoring; and Integration. **Please use the techniques that you 
   deem applicable to your problem. You need to convince us in the report why you decided to 
   use/exclude some techniques.**
* This project emphasizes the sound, systematic analysis of the presented problem, the associated 
solution space, and the chosen solution(s). The software reengineering sessions are composed in 
such a way as to prepare you for such a project. We stimulate you to assess the benefits and 
drawbacks of the techniques presented in the lab sessions and ask you to exploit the analysis 
techniques wisely. You are free to use alternative analysis techniques and tools as much as you 
deem necessary. 
* What concerns the refactoring-part, we emphasize the use of tests. Our minimum requirements are:
  * Determine the extent to which the current tests provide feedback on your future refactoring-steps. 
  Quantify this (i.e., show coverage information).
  * Compose an argument discussing why the tests are adequate/inadequate for your chosen 
  refactoring scenario. If inadequate, adjust the tests as needed. Be efficient with regard 
  to the time invested in testing. 

### 5. General Evaluation
To show that you have passed the assignment, you will have to demonstrate the following:

* You possess the knowledge to plan and selected the appropriate reengineering patterns for your project activities.
* You have made a selection of analysis techniques (e.g., code integration, mining software 
repositories, metrics and visualization as seen in the lab sessions, but others are allowed 
as well), and have applied these techniques in a sound, systematic manner. You have indicated 
clearly (using screenshots, results of the interpretation of the output of the techniques) 
how you have used the results of these analysis techniques.
* You have performed the above activities (decomposed into (i) Design Recovery; (ii) Redesign; 
(iii) Management; and (iv) Refactoring) and discussed them in your project report.
* The restructurings you have applied are behavior preserving:
  * You can demonstrate the mapping between each of the classes from the original structure 
  with the new structure.
  * The compilation process succeeds flawlessly.
  * The tests run without flaws and show increased testing coverage making it more reliable.
* The introduction of the new design clearly indicates the project is ready to be released in a 
language of choice. You are not supposed to carry out the refactoring process completely. 
Select and execute a set of refactorings that sufficiently illustrate your proposed solution.
* The report is written in a clear manner detailing all the steps and reasoning for the project. 
Remember that the report is the document that registers all your work. Thus, it is the most 
important artifact for the evaluation process.

For a more precise on-point view of the evaluation criteria, please look over the check-list 
(for each report) on the course's main page.

### 6. Report 
Aspects that we typically like to see addressed in the final report are:
* **Context**: Briefly discuss the context in which you are running your project (do not just 
copy verbatim the text on 1. Contextualization).
* **The Problem at Hand**: Clarify the problem at the base of the project, and indicate its 
intrinsic difficulties (again, do not just copy the assignment problem description, elaborate 
based on your chosen interpretation, goals, and scope).
* **Reengineering Patterns**: You explicitly state the patterns (from the OORP book) that you 
selected and used throughout the project.
* **Project management**: Demonstrate how you have organized the work, and how you are controlling 
it (instead of the work controlling you!)
  * **Scope**: What are the boundaries of your project? What is not included in the project?
  * **Risks**: Which risks were envisioned, and which have been mitigated? What is the priority 
  of the risks that still need to be mitigated? E.g., which external dependencies might have an 
  effect on your outcome? Which alternatives have you prepared in case this risk instantiates?
* **Software reengineering**:
  * **Tests**: How can you verify that you satisfy the requirements? Which testing strategy have 
  you selected, and what are the arguments for this selection? How confident are you that your 
  solution satisfies the requirements?
  * **Quality assurance**: What are the non-functional requirements? E.g., how do you differentiate 
  between a good and a bad solution?
  * **Refactoring**: Which refactorings did you perform on the project? Why is it better now? 
  How does your refactoring help to support the new intended features?

Those are aspects we like to see addressed/tackled/discussed/explained/presented in the Final 
Report. In the Intermediate Report, we expect less detail. However, groups that try to start 
addressing some of the above concerns most often have a better Intermediate Report. In the 
Pre-conditions Report, although not necessary, it might be better if your group starts to plan 
the scope and goals for the project.

Please also keep in mind and check the Report Guidelines and the Evaluation Checklist on the main page.

### 7. Final Remarks
If you have any questions about the project or the report, please contact me.







 





















 

















