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


Senior Design Ideas submitted to CoE
=====
Please take a look at some Senior Design ideas submitted to the College of Engineering.
[SD Ideas to be updated]()

Subway Simulation
=======
* Functional Requirements:
  * Specification 1.0 [[pdf](../../../files/472Files/specification1.0.pdf)]
  * Specification 2.0 [[pdf](../../../files/472Files/specification2.0.pdf)]

Traffic Simulation
========
* Functional Requirements:
  * Specification 1.0 [[pdf](../../../files/472Files/Traffic_simulationSpec1.0.pdf)]
  * Specification 2.0 [[pdf](../../../files/472Files/Traffic_simulationSpec2.0.pdf)]


To see how things work in concrete terms, you will find the form below with the assessment criteria.

Evaluation criteria 472 [[Google Doc](https://docs.google.com/document/d/1AhUVxWgfDtQVmgEJD0acVPnD72SRoKTHJ2Qh5X6IPqY/edit#)]

Deliverables
========
The following documents will guide you produce the deliverables of the project:
* Precondition report ([Doc](https://docs.google.com/document/d/1tLiXVKfddl_lBFB0id7Wr_jb-19wDip664vMxTusj34/edit))
* Design Portfolio I ([Doc](https://docs.google.com/document/d/1y9Fl1yHl8S3Uh3TzEdQYhd7bQUkYVwZTEcB4H43SlvE/edit#))
* Design Portfolio II ([Doc](https://docs.google.com/document/d/1mUBX7hakgAdiBDJv9HPzD9436Ezvr2nPeZkdk9psGa8/edit#))
* Design Portfolio III ([Doc](https://docs.google.com/document/d/13xShWs_zi9bBmfkToTYu4v68KwVXHZOjAdw7-obOIgg/edit))
* Presentation ([Doc](https://docs.google.com/document/d/16m2-bSjpR60oA6FKyxBqAdArVKCH9HkUy1foDuK7CfA/edit))

  
Instructions to the UML Diagrams
=========
You will use simple **use case diagrams**, **class diagram** and **sequence diagrams** or any other UML diagrams you find suitable.
A simple class diagram has only the name of the class and its interactions with the other classes 
(there are two examples in [JPacman](https://github.com/johnxu21/jpacman/tree/master/doc/uml) repository in the "docs" folder). 
This is to reinforce your initial understanding of the 
system. You only need to focus on the classes associated with the feature/use case and the classes that are 
called in those classes. There is no need to go deeper into the class structure (i.e., if feature 
class calls Class X, and Class X calls Class Y, then you do not need to show Class Y since it is 
not being called directly by the feature class you are implementing). I am are not going to evaluate your strictness to the 
proper UML notations, therefore focus on modeling and understanding classes interactions. 

### 3. General Coding Instructions
The following coding/repository instructions apply:
* Fork the group repository and clone that fork onto your local repository.
* Create a branch on your fork for every "qualified contribution" you would like to make on the group/main repository. 
For example, if you have been assigned to develop **UC-2.1**, create a branch on your fork called  **UC-2.1**. 
If you are fixing a bug on the main repository, name the branch with an appropriate name. If you are introducing missing 
tests, also name the branch name appropriately.
* All the contributions to the main repository have to be submitted through pull requests that at least two other group members should have review.
* The group should explicitly set **contribution guidelines** that the team members should follow. The 
reviewers should resolve pull request only if the guidelines have been followed.

### 4. Code Review

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

Correctness, Readability , Design , Style, Functionality, Complexity, Consistency

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



### 5. Weekly Group Meetings
A template for the minutes can be found [here](https://docs.google.com/document/d/1bq32N9LfLpy4ogQ7UOonJxeK8di6-GyuSPCGBUecLoE/edit) 
