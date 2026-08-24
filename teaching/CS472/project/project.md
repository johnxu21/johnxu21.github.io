---
layout: page
title: Project
permalink: /teaching/CS472/project/
---

<div class="main-component">
<form action="/teaching/CS472/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>

<form action="/teaching/CS472/Timetable/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Timetable" />
</form>
<form action="/teaching/CS472/Exam/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Exam" />
</form>
<form action="/teaching/CS472/project/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Project" />
</form>
</div>
<br/>

<div class="main-component">
<form action="/teaching/CS472/project/Group/">
    <input type="submit" style="background-color:#008CBA;float:left; color:white;width:130px;
height:30px;" value="Groups" />
</form>
<form action="/teaching/CS472/project/FAQ/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="FAQ" />
</form>
<form action="/teaching/CS472/project/Presentations/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="Presentations" />
</form>
<form action="/teaching/CS472/project/Clients/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="Client Projects" />
</form>
<form action="/teaching/CS472/project/Competition/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="SD Competition" />
</form>
</div>

<br/>
<br/>

Project
=========

Groups will develop their custom projects. The groups will also deliver a specification document along with Design Portfolio I. You can borrow a leaf from the specification documents for the two projects below. The quality of the group’s specification document does not have to be like the ones presented but should be reasonable. I will review your Specification documents to approve the group’s custom project.


Subway Simulation
======

* Functional Requirements:
  * Specification 2.0 [[pdf](../../../files/472Files/specification2.0.pdf)]

Traffic Simulation
========

* Functional Requirements:
  * Specification 2.0 [[pdf](../../../files/472Files/Traffic_simulationSpec2.0.pdf)]


To see how things work in concrete terms, you will find the form below with the assessment criteria.

Weekly Group Meetings:
====

A template for the minutes can be found [here](https://docs.google.com/document/d/1bq32N9LfLpy4ogQ7UOonJxeK8di6-GyuSPCGBUecLoE/edit) 


Deliverables
=====

The following documents will guide you produce the deliverables of the project:
* Precondition report ([Doc](https://docs.google.com/document/d/1tLiXVKfddl_lBFB0id7Wr_jb-19wDip664vMxTusj34/edit)) **- Sept 4th 2026**
* Design Portfolio I ([Doc](https://docs.google.com/document/d/1y9Fl1yHl8S3Uh3TzEdQYhd7bQUkYVwZTEcB4H43SlvE/edit#)) **- Sept 25 2026**
* Design Portfolio II ([Doc](https://docs.google.com/document/d/1mUBX7hakgAdiBDJv9HPzD9436Ezvr2nPeZkdk9psGa8/edit#)) **- Oct 25th 2026**
* Design Portfolio III ([Doc](https://docs.google.com/document/d/13xShWs_zi9bBmfkToTYu4v68KwVXHZOjAdw7-obOIgg/edit)) **- Nov 29th 2026**
* Presentation ([Doc](https://docs.google.com/document/d/16m2-bSjpR60oA6FKyxBqAdArVKCH9HkUy1foDuK7CfA/edit)) **- Nov 30th 2026**

Design Portfolio Evaluation 
=====

* Design Portfolio I ([Doc](https://docs.google.com/document/d/15HKZ10h56K-V7aLgyaN5e4hQ6GHTeGHc0BLzVsXhofU/edit))
* Design Portfolio II ([Doc](https://docs.google.com/document/d/10qp_z0OMqyIvfSuUjU-3hKK0v3G5s9DhNuVhoASBjGk/edit))
* Design Portfolio III ([Doc](https://docs.google.com/document/d/1APCK159uvnm7XuY8d4N_JQ7sZ4VDrencIXrrtzRrkHE/edit))


# 1. Team Collaboration and Assessment Requirements:

Each team member will be assessed based on their active participation in the collaborative development process. The assessment criteria include the following:

1. **Meaningful Pull Requests:** Each team member must contribute a **minimum of 6** meaningful pull requests throughout the project duration. A meaningful pull request is defined as one that adds value to the project, such as implementing a new feature, fixing a bug, or improving code quality.
2. **Meaningful Peer Reviews:** Additionally, each team member is required to conduct a **minimum of 6** meaningful peer reviews. Peer reviews can be performed on issues or pull requests raised by other team members. A meaningful peer review involves providing constructive feedback, suggestions for improvement, and ensuring adherence to project guidelines.
3. **Distribution of Contributions:** To ensure balanced participation, team members should aim to have **at least 3** meaningful pull requests and 3 meaningful peer reviews in Design Portfolio II, and the remaining 3 of each in Design Portfolio III.
4. **Clear Guidelines for Contributions:** Team members are encouraged to establish clear guidelines for meaningful contributions, starting from the logging of feature requests as issues. When submitting pull requests, they should thoroughly develop the requested feature, fix, or improvement and link the pull request to the corresponding issue for proper tracking and reference. Additionally, reviewers should carefully consider whether the issue has been adequately addressed before approving and merging the pull request.
5. **Review of AI-Generated Code:** Reviewers should also ensure that contributors have followed the instructions for AI-generated code integration, as outlined in the project guidelines. This includes verifying the presence of annotations within the code comments, indicating the type of generator used and the level of human intervention performed (see [Instructions for AI-Generated Code in Team Projects](#instructions-for-ai-generated-code-in-team-projects) section).



# 2. Design Diagrams and Development Process

Design diagrams should help the team understand important system decisions before implementation and keep the documented design aligned with the code.

Not every feature or pull request requires a new diagram. Create or update a diagram when the work introduces a meaningful change to the system’s structure, behavior, architecture, or interaction with external components. Testing, documentation, CI configuration, minor bug fixes, and small refactoring contributions may not require diagrams.

## Design Expectations

- Maintain a current **architectural overview** showing the system’s major components and their relationships.
- Use focused diagrams for features that involve important structural or behavioral decisions.
- Update existing diagrams when implementation changes the documented design.
- Keep diagrams lightweight and limited to the components needed to explain the decision.
- Use diagrams during team discussions and pull-request reviews when they help reviewers understand the proposed change.

The intended traceability is:

**Requirement → Design → Issue/PR → Code → Tests/CI**

## Selecting an Appropriate Diagram

Choose the diagram type that best communicates the design:

- **Use Case Diagram:** Shows how users or external actors interact with the system. Use it to clarify system scope and major user goals.
- **Class or Component Diagram:** Shows structural relationships among classes, modules, services, or components. Include only the elements relevant to the feature or decision being explained.
- **Sequence Diagram:** Shows the order of interactions among objects, services, or components during an important workflow.
- **Activity Diagram:** Shows a workflow, decision process, or sequence of activities.
- **Other Models:** Another suitable modeling approach may be used when it communicates the design more effectively.

A feature does not require both a structural and behavioral diagram unless both are necessary to explain the design.

## Guidelines

- **Start simple:** Show the important components and relationships first. Add detail only when it improves understanding.
- **Model the current system:** Diagrams should reflect implemented or approved design decisions rather than unsupported future ideas.
- **Focus on relevant elements:** Do not redraw the entire system when only a small part has changed.
- **Support different technologies:** Class diagrams may not be appropriate for every project. Component, sequence, activity, data-flow, or other diagrams may be more useful for functional, JavaScript/TypeScript, service-based, or data-intensive systems.
- **Prioritize communication:** Strict UML notation is not the primary grading concern. Diagrams must be accurate, understandable, and useful to the team.
- **Collaborate:** Important design decisions should be discussed with the team rather than developed independently by one contributor.

## Repository and Pull-Request Integration

- Store design diagrams in a clearly identified location in the team repository or shared design document.
- Use descriptive file names and keep diagrams under version control whenever practical.
- When a pull request implements or changes a documented design decision, include a link to the relevant diagram in the PR description.
- If the implementation differs from the original design, update the diagram and briefly explain the reason for the change.
- Diagrams are not required for every PR. Include them only when they provide useful context for understanding or reviewing the contribution.

## Design Portfolio Evidence

In Design Portfolio II, teams will select **two representative implemented features** and show how each connects to its requirement, design, issue or pull request, code, and test or CI evidence. Detailed instructions are provided in the Design Portfolio II requirements.

The goal is to make design a practical part of development and review—not to produce diagrams merely to satisfy a documentation requirement.# 3. Project Development Workflow

All project contributions must follow the team’s GitHub workflow:

1. Select or create an issue with a clear description and acceptance criteria.
2. Fork the team repository and keep your fork synchronized with the team repository.
3. Create a focused branch with a descriptive name.
4. Implement and test the change.
5. Open a pull request linked to the issue.
6. Request a review from the assigned teammate.
7. Address the reviewer’s feedback.
8. Merge only after receiving at least one approval and passing the required CI checks.

Keep pull requests focused. Unrelated changes should be submitted separately.

During Design Portfolio II and Design Portfolio III, start contributing early. Aim to submit approximately **one meaningful pull request per week** rather than waiting until the portfolio deadline.

# 4. Issues and Pull Requests

## Issues

Use issues to define and track project work. An issue should include:

- A clear description of the problem, feature, or task.
- Relevant context, screenshots, error messages, or code links.
- Acceptance criteria describing when the work will be considered complete.
- Any important constraints or dependencies.

Use the team’s issue templates when available.

## Pull Requests

A pull request should:

- Explain what changed and why.
- Link to the corresponding issue.
- Describe how the change was tested.
- Include relevant screenshots, output, or CI evidence when appropriate.
- Identify any known limitations or remaining work.

Draft pull requests may be opened early when feedback would help guide the implementation.

# 5. Peer Review

Every pull request must receive at least one teammate’s approval before it is merged.

When reviewing a pull request, consider:

- Does the change address the linked issue and its acceptance criteria?
- Is the implementation correct, understandable, and appropriately scoped?
- Are relevant tests included, and do the CI checks pass?
- Does the change follow the project’s design and coding conventions?
- Are documentation or diagrams affected by the change?
- Are there unnecessary or unrelated modifications?

Reviews must be constructive and evidence-based. Clearly distinguish between:

- **Required changes:** Must be addressed before approval.
- **Suggestions:** Recommended improvements that do not block approval.
- **Questions:** Points requiring clarification or discussion.

Review assigned pull requests promptly. Delayed reviews can block teammates and slow the entire project.

# 6. Team Collaboration

Teams must:

- Hold at least one project meeting each week.
- Record decisions, assigned tasks, and task completion in the meeting-minutes document.
- Use issues and pull requests to make work visible to the team.
- Communicate blockers as soon as they arise.
- Share technical knowledge and avoid concentrating essential system knowledge in one person.
- Coordinate work to reduce conflicts and support integration.

The team is collectively responsible for delivering an integrated and tested MVP.

# 7. Use of Generative AI Tools

Students remain responsible for understanding, testing, reviewing, and validating all work submitted to the project.

If generative AI tools are used:

- Follow the course policy.
- Disclose their use in the required project documentation.
- Verify generated code before submitting it.
- Do not submit code that you cannot explain or maintain.
- Ensure that AI-assisted contributions satisfy the same review, testing, and quality requirements as other contributions.

Generative AI output is not evidence that a feature works. The implementation must still be reviewed, tested, and verified through the team’s normal development process.

