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

<form action="/teaching/CS472/project/Competition/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="SD Competition" />
</form>
</div>

<br/>
<br/>

Project 2022-2023
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
* Precondition report ([Doc](https://docs.google.com/document/d/1tLiXVKfddl_lBFB0id7Wr_jb-19wDip664vMxTusj34/edit)) **- Jan 31st, 2025**
* Design Portfolio I ([Doc](https://docs.google.com/document/d/1y9Fl1yHl8S3Uh3TzEdQYhd7bQUkYVwZTEcB4H43SlvE/edit#)) **- Feb 18th 2025**
* Design Portfolio II ([Doc](https://docs.google.com/document/d/1mUBX7hakgAdiBDJv9HPzD9436Ezvr2nPeZkdk9psGa8/edit#)) **- March 24th 2025**
* Design Portfolio III ([Doc](https://docs.google.com/document/d/13xShWs_zi9bBmfkToTYu4v68KwVXHZOjAdw7-obOIgg/edit)) **- May 5th 2025**
* Presentation ([Doc](https://docs.google.com/document/d/16m2-bSjpR60oA6FKyxBqAdArVKCH9HkUy1foDuK7CfA/edit)) **- May 6th 2025**

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



# 2. Instructions to the UML Diagrams and Design Process

Before authoring a pull request for any new feature or use case, **at least one design diagram** should be created to model how the feature interacts with the rest of the system.

You may use **use case diagrams**, **class diagrams**, and **sequence diagrams**, or any other UML diagrams you find suitable to represent your feature. The purpose of these diagrams is to **reinforce your understanding of the system** and how different components interact with each other.

## Guidelines:
- **Minimum Requirement**: Each feature or use case must be represented by at least one design diagram (use case, sequence, or class diagram). Select the type of diagram that best illustrates how your feature interacts with other system components.
  - For **non-object-oriented projects** (such as JavaScript/TypeScript), where class diagrams may not always be applicable, you may focus on sequence diagrams or use case diagrams to represent interactions.
- **Focus on Interaction**: The goal of the design diagram is to ensure that you fully understand how the feature or use case interacts with other components before implementation. This also ensures that team members can easily follow your thought process when reviewing pull requests.

## Diagram Guidelines:
- **Use Case Diagrams**: These represent the interactions between the users (actors) and the system. Keep them simple and focused on the specific feature you are developing.
- **Class Diagrams**: A simple class diagram should include the **class name** and its **interactions with other classes**. There is no need to detail every attribute and method—just focus on the relationships (associations, dependencies, etc.) between classes.
  - You only need to show the classes directly involved with the feature or use case. If **Class X** calls **Class Y**, but **Class Y** is not directly related to your feature, you don’t need to show **Class Y**.
- **Sequence Diagrams**: These should capture the **flow of interactions** between different objects or components within the system. Focus on how messages or function calls are passed in sequence during the execution of your feature.

## Tips:
- **Start Simple**: Diagrams are meant to help you understand the system. Begin with simple diagrams that show key interactions, and add more detail if needed.
- **Collaboration**: Work with your team to ensure everyone shares the same understanding of how different components interact. Use diagrams to facilitate these discussions.
- **Diagram Selection**: Choose the type of diagram that best represents your feature. For example, if a class diagram doesn’t make sense, a sequence diagram or use case diagram might better illustrate the interaction.
- **No Strict UML Notation**: I’m not evaluating strict adherence to UML syntax, so focus on **modeling and understanding** class interactions and system components rather than perfect UML representation.

## Repository Structure & Pull Requests:
- **Repository Structure**: Maintain a clear folder structure in the repository for design diagrams, with folders organized by features or use cases. This will make diagrams easy to locate and understand.
- **Pull Requests**: When submitting a pull request (PR), include a link to the corresponding design diagram in the PR description. This will help reviewers understand the feature or use case in context.

By following these structured guidelines, you ensure that design thinking is prioritized while keeping the process streamlined and manageable.
 

# 3. General Coding Instructions

The following coding and repository instructions apply:

- **Fork the group repository** and clone your fork to your local machine.
- **Create a branch** on your fork for every "qualified contribution" you plan to make on the group/main repository.
  - For example, if you're assigned to develop **UC-2.1**, create a branch named **UC-2.1** on your fork.
  - If you're fixing a bug on the main repository, use a descriptive name for the branch (e.g., **bugfix-login-error**).
  - If you're adding missing tests, name the branch accordingly (e.g., **add-missing-tests**).
- **Submit all contributions** to the main repository through pull requests (PRs), which should be reviewed by at least two other group members.
- The group should establish **clear contribution guidelines** for all members to follow. Reviewers should only approve pull requests if these guidelines have been followed.


# 4. Examining Issues
An issue is a way to discuss, plan and track work on a GitHub repository.

Issues can be bugs, complaints from users, requests for new features or added functionality.

When reading through an issue, these are some of the questions that can guide you.
* Are there multiple problems reported in the issue?
* Can you confirm the issue by reading the code or documentation?
* Do you need to run the code to confirm the issue?
* Can you reproduce the problem?

Issues are used to describe the problem. 
The issue should contain a link to the code under discussion, and some questions to think about when looking at the issue, 
the code, and the pull request.

 Best practices when reporting an issue
====

You team repo should use [GitHub issues templates](https://code-review.org/docs/exercises/examine-issues/) to prompt people to provide relevant information

What is important information you would like to someone to give in an issue?

* version of the code being used?
* a small example the shows the bug?
* screenshots of the problem?
* error messages?
* desired solution?
* operating system where the problem occurred (Windows, Mac, Linux)?
* does the issue describe the problem accurately?


# 5. Working with Pull requests
A pull request is a proposed change. A review is feedback on the change.

When you are reviewing, you’ll need to assess the scope and size of the pull request. This will give you some 
idea of how much work will be involved in the review, and what feedback you need to give.

Read the pull request description. Ideally this will give you the scope:
* What’s changed.
* Why the changes were made.
* What the person is looking for from the review. They may have code ready to release, they may have an urgent bug fix, they may have a draft that they want you to look at before they do any more work.

Small code changes can have big impacts, so lines of code changed does not necessarily correlate with how difficult, important, or necessary a change is. But you can use GitHub to see:
* How many lines of code have been added or removed.
* How many files have been changed.
* How many commits were made.

The pull request is a solution to the issue.
Review the pull request, does the pull request fix the issue?

* Add comments about what is good, what is bad.
* Add suggestions for code changes.
* Would you accept the pull request as is? If not, why not.

### Adding comments 
To add a comment, click on the `+` or `-` by the line number. A blue box `+` will show up when you hover over 
a `+` or `-`. You can only comment on the green (new lines of code) or red (code removed) sections.

### Adding suggestions 
Suggestions are the same as comments, but you suggest an edit to the code that can be committed from the pull request. 
Click the suggestion icon in the comment box:


# 6. Code Review

What is the goal of code review?
====

* Reviewing can be challenging, requiring thoughtful consideration of how to effectively communicate constructive and actionable criticism.
* Become more comfortable having your code reviewed. People will explain a scientific idea with a sketch on a whiteboard, or a napkin no problem. But when it comes to code, there is a real tendency to keep it hidden. You might have heard people say, “oh I need to polish this before I show it to you.” There is some psychological effect behind this, and it would be great to change this and get people showing even pseudo code to each other. Sharing early and often becomes second nature.
* Use code review as a collaboration tool. Use code review as part of your onboarding new team members and collaborators. Share knowledge and know-how between team members. There is a real benefit to being on both sides of the review. We’re trying to humanize this process, and build rapport between people.
* Read more code than you write! Take a peek into your favorite open source tools. Encourage people to have a look inside the software they are using. How does this work? Why did they do this?

When reviewing:
====

Does the pull request address the issue?
* Are there any deal breakers that would stop you accepting the changes?
* Can you suggest any improvements?
* What is a good way to phrase your suggested improvements?
* Is the solution overly complicated? For an example of an overly complicated solution, see the [famous fizz buzz in Tensorflow](https://joelgrus.com/2016/05/23/fizz-buzz-in-tensorflow/).
* Are the comments up to date, necessary, helpful?
* Would you except the pull request as it is now? Are your suggested changes must-do? nice-to-have? nitpicks? How would you communicate this?
* Do you spend a lot of time reviewing the code style? Is it worth having a style guide for contributors? Can you make use of an existing style guide? Or a linter?

When working on your own contributions:
* When putting in a pull request, how can you make it easy for a reviewer to understand what you have done?
* What makes a good pull request, what makes a bad pull request?
* Can you commit code in a way that lets someone review your code more easily? Should you separate functional changes from style changes? Would you use a tool such as [commitizen](https://commitizen.github.io/cz-cli/) to prompt yourself at commit time? Why? Why not?

How do you tell if code is better?
====

* Correctness
* Readability
* Design
* Style
* Functionality
* Complexity
* Consistency

Depending on your experience you may focus on one, many, or all of these.

The main question to ask yourself when reviewing code is:

Does the pull request improve the existing code?

* Are there unnecessary changes? If the pull request contains other changes that are not related to the issue, how does your team deal with this. It is ok to close the pull request?
* Is now a good time to add new functionality?
* Does the code do what it says it does?
* What testing has been carried out?
* What dependencies does the code have? Are they required? Are they secure? Are they manageable?
* How does the code handle errors?
* Does the new code change how users interact with the software? Does this require a change to the documentation?
* Did the author write comments? Do the comments match the code? Are all the comments necessary and helpful?
* Does the author follow the style of the rest of the code? Do you have a style guide?
* Can I accept the pull request as-is, or are there changes that must be made?

# Giving Feedback 
When giving feedback on code, try to give comments that:

* are actionable.
* differentiate between a suggestion, a definite change, or a point that needs a discussion or clarification.
* are collaborative not accusatory.

# How do organizations decide if code is better? 
Take a look at organizations you admire or appreciate. What practices do they employ for code review? Below are some examples of code review guides from well known organizations.

[Google eng-practices](https://google.github.io/eng-practices/review/reviewer/looking-for.html)

[Microsoft Code with Engineering Playbook](https://microsoft.github.io/code-with-engineering-playbook/code-reviews/)

[Python Discord, Code Reviews: A Primer](https://www.pythondiscord.com/pages/guides/pydis-guides/code-reviews-primer/)


# 7. Guidance for MVP Development: Fostering Collaboration to Mitigate Challenges

As you embark on the development of your minimum viable product (MVP), fostering collaboration among your team members will be crucial to overcoming challenges and maximizing the effectiveness of ChatGPT usage. Here are some key points to consider:

## Leveraging Collaboration Platforms:

1. **Issue Discussions**: Utilize issue discussions on your project repository to openly communicate about the integration of ChatGPT into your software development process. Encourage team members to share their insights, questions, and solutions related to ChatGPT usage.
2. **Pull Requests**: When submitting pull requests that involve ChatGPT-generated code or contributions, actively seek feedback from your teammates. Peer review not only ensures the quality of the code but also promotes knowledge sharing and collaborative problem-solving.
3. **Team Meetings**: Schedule regular team meetings to discuss ChatGPT usage strategies, share experiences, and address any challenges or uncertainties collectively. These meetings provide a platform for collaborative decision-making and learning from each other's perspectives.

## Sharing Insights and Learnings:

1. **Documentation**: Document your ChatGPT interactions and findings in the project repository. Share your experiences, best practices, and any lessons learned with your team members to facilitate knowledge exchange and learning.
2. **Feedback Loop**: Establish a feedback loop within your team to continuously evaluate the effectiveness of ChatGPT usage and identify areas for improvement. Encourage open communication and constructive feedback to iteratively enhance your approach.
3. **Resource Sharing**: Share useful resources, tutorials, or examples related to ChatGPT and software engineering tasks with your team members. Collaboratively explore additional tools or techniques that complement ChatGPT and enhance your development process.

## Instructions for AI-Generated Code in Team Projects

As part of your team projects, you have the option to leverage AI-generated code to facilitate software development tasks. However, it is essential to maintain transparency and documentation regarding the use of such code within your project repositories.

1. **Annotation Requirement:** When integrating AI-generated code into your project, each team member must annotate the code snippets with relevant information describing the generative model used and the level of human intervention performed on the code. This annotation should be included directly within the code comments.
2. **Annotation Format:** Follow the annotation format outlined below:
   - Use the comment markers `// ai-gen start` and `// ai-gen end` to encapsulate the AI-generated code section.
   - Within the AI-generated code section, specify the following information:
     - Type of generator used (e.g., ChatGPT-3.5, ChatGPT-4).
     - Level of human intervention:
       - Level 0: No intervention (code used directly with zero changes).
       - Level 1: Minor intervention (code used with ≤ 10% of lines changed).
       - Level 2: Major intervention (code used with > 10% of lines changed).
3. **Example Annotation:** Refer to the example below for annotating AI-generated code:
   ```cpp
   // ai-gen start (ChatGPT-3.5, 0)
   // Insert AI-generated code here
   // ai-gen end
   ```
   
```python
   # ai-gen start (ChatGPT-3.5, 0)
   def fibonacci(n):
       if n <= 1:
           return n
       else:
           return fibonacci(n-1) + fibonacci(n-2)
   # ai-gen end
```

**Data Collection:** The annotations serve as a means of tracking and documenting the integration of AI-generated code into your project. Ensure consistency in annotation format and placement to facilitate automated data collection at key project milestones.

By adhering to these guidelines, you promote transparency and accountability in the utilization of AI-generated code while ensuring proper documentation for project evaluation and assessment.


