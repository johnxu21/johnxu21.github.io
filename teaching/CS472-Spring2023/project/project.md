---
layout: page
title: Project
permalink: /teaching/CS472-Spring2023/project/
---

<div class="main-component">
<form action="/teaching/CS472-Spring2023/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>
<form action="/teaching/CS472-Spring2023/study_material/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Study Material" />
</form>
<form action="/teaching/CS472-Spring2023/Timetable/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Timetable" />
</form>
<form action="/teaching/CS472-Spring2023/Exam/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Exam" />
</form>
<form action="/teaching/CS472-Spring2023/project/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Project" />
</form>
</div>
<br/>

<div class="main-component">
<form action="/teaching/CS472-Spring2023/project/Group/">
    <input type="submit" style="background-color:#008CBA;float:left; color:white;width:130px;
height:30px;" value="Groups" />
</form>
<form action="/teaching/CS472-Spring2023/project/FAQ/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="FAQ" />
</form>
</div>

<br/>
<br/>

Project 2022-2023
=========
Two projects with their specification documents have been prepared for you. You are free to choose any of them. 
The projects are of equal strength, so it would be nice if they are distributed equally between the groups. 
Groups are also free come up with their own custom projects. However, If you choose to work on a custom project, 
then you will need to explain/motivate why this project would allow you to demonstrate your software 
engineering skills. You will also prepare a specification document with in the first three weeks of the class.
You can borrow a leaf from the specification documents for the two projects below. The quality of the group's
specification document does not have to be like the ones presented, but should be reasonable.
I will to look at your Specification documents to approve the groups' custom project.

Senior Design Ideas submitted to CoE
=====
Please take a look at some of the Senior Design ideas submitted to the College of Engineering.
[SD Ideas](https://mail.google.com/mail/u/3/#inbox/FMfcgzGrcPGBvpMsrnHFgQTljvFVzgjq?projector=1&messagePartId=0.1)

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


Other Requirements
[Non Functional Requirements](/teaching/CS472-Spring2023/project/nfr/)
  * [C++ Code Conventions](/teaching/CS472-Spring2023/study_material/material/CMakeLists.txt)

To see how things work in concrete terms, you will find the form below with the assessment criteria.

Evaluation criteria 472 [[Google Doc](https://docs.google.com/document/d/1AhUVxWgfDtQVmgEJD0acVPnD72SRoKTHJ2Qh5X6IPqY/edit#)]

[comment]: <> (Use this code below to extract graphs for the contributions of each group member)

[comment]: <> (* [Contributions]&#40;https://github.com/johnxu21/msrLab/blob/main/src/Workload.ipynb&#41;)

Deliverables
========
The following documents will guide you produce the deliverables of the project:
* Design Portfolio I ([Doc](https://docs.google.com/document/d/1y9Fl1yHl8S3Uh3TzEdQYhd7bQUkYVwZTEcB4H43SlvE/edit#))
* Design Portfolio II ([Doc](https://docs.google.com/document/d/1mUBX7hakgAdiBDJv9HPzD9436Ezvr2nPeZkdk9psGa8/edit#))
* Design Portfolio III ([Doc](https://docs.google.com/document/d/13xShWs_zi9bBmfkToTYu4v68KwVXHZOjAdw7-obOIgg/edit))
* Presentation ([Doc](https://docs.google.com/document/d/16m2-bSjpR60oA6FKyxBqAdArVKCH9HkUy1foDuK7CfA/edit))

Getting Started Instructions
=======
Please pay attention to the following instructions. The group leader should send an email to <em></em><a href="mailto:john.businge@unlv.edu">me</a> with:
* Subject "SDD - Project". 
* Message Body:
  * The full name of the members in your group.
  * Attach the **pre-conditions report** (PDF format) in your message.

* Your Pre-conditions Report should contain the following:
  * Project Name
  * Full names of all the members in your group
  * A link to the groups GitHub repository
  * The members are set as collaborators to the GitHub project.
  * Invite me as collaborator on your repository. (my [GitHub ID - ```johnxu21```](https://github.com/johnxu21)).

Instructions to the UML Diagrams
=========
You will use simple **class diagram** or **sequence diagrams** or any other UML diagrams you find suitable.
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