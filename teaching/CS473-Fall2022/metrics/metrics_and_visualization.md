---
layout: page
title: Metrics and Visualization
permalink: /teaching/Software-Reengineering/metrics/
---

<form action="/teaching/Software-Reengineering/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>
<form action="/teaching/Software-Reengineering/metrics/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Metrics and Visualization" />
</form>
<form action="/teaching/Software-Reengineering/refactoring/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Refactoring Assistants" />
</form>
<form action="/teaching/Software-Reengineering/integration/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Software Integration" />
</form>
<form action="/teaching/Software-Reengineering/dynamic/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Dynamic Analysis: Testing" />
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

<p align="justify"/>

The purpose of the laboratory exercises in general is to stimulate discussion about the properties of a well-structured object-oriented design. The tasks and assignments are designed to stimulate your comprehension of the topic and the tools. In most cases, you can use alternative projects and/or tools to accomplish the same or similar tasks, or even more!
<br/>
This session is to provide you the first contact with the sample projects and tools. Consider the tools used in this session as the providers of data required to build up an argument for a system report or action plan.
<br/>

Sample Projects and Tools
========
* Lecture Sides [here](../../../files/metrics_and_visualization.pdf)
Projects
* [pacman-python](https://github.com/Software-Reengineering/pacman-python) 
* [django CMS](https://github.com/django-cms/django-cms)
IDE
* [PyCharm](https://www.jetbrains.com/pycharm/) 
Tools
* [CodeScene](https://codescene.com/) - **no** installation necessary, but it requires a GitHub account. This tool integration with GitHub allows it to visualize your repositories.
* [JsCity](https://github.com/ASERG-UFMG/JSCity/wiki/JSCITY) is an implementation of CodeCity to analyze JavaScript code.
Book
* Object-Oriented Reengineering Patterns (OORP - http://scg.unibe.ch/download/oorp)

<br/>


Setup / Preparation
=============

First, fork a project that you want to analyze into your GitHub account. This is necessary because the free version of CodeScene can only see projects in your own account.

Second, go into CodeScene, and click on the "Login" menu (top-right corner). You can choose the option "Login with Github". Once logged in, you can choose to create a new project, where CodeScene will show all the GitHub projects in your account. Select Pacman and go do the next part until it finishes (it might take a while, depending on the project). 


Download/Clone the same project and open it on the IDE of your choice (for example, PyCharm). Build and run the project. Refer to the additional documentation if necessary.


Also if have not already, download the book for this course "[Object-Oriented Reengineering Patterns](http://scg.unibe.ch/download/oorp/)" (Note: OORP, p.xx refers to a page in the pdf version of this book)
<br/>

Task 1: Introduction (React)
============
This first task has two goals: 
* to help familiarize yourself with the CodeScene interface; and 
* to observe that not every visualization is useful for refactoring.

Visit the [CodeScene](https://codescene.com/) website and click at the Showcases. These are examples (from a full version of CodeScene and not only the free version we are using) of projects analyzed by CodeScene. Select the React project and look at the visuals presented.

Visit the [JsCity](https://github.com/ASERG-UFMG/JSCity/wiki/JSCITY) website and look at the examples. You may want to select a simple example first to get acquainted. But after that, also select the "React" project to visualize (and be patient because it may take a while). 

What did you think of these visualization tools? Can you extract important information about the visualized project from them? Which visualization would be more useful to plan refactoring activities?
<br/>

Task 2: Hands-on -- pacman-python
===============
For the second task, the goal is to start getting acquainted with pacman-python source code. 
Download/clone the repository and run the application. Now look at the source code and 
other files in the project. Try to understand its internal structure.

As stated in the book (OORP, p.39), this is your "**First Contact**" with the software that needs 
reengineering activities. As often we ask ourselves "**Where do I start?**" (OORP, p.40).

Well, pacman-python  is a Python implementation that is supposed to replicate the original [Pacman Game](https://en.wikipedia.org/wiki/Pac-Man). What features are missing in pacman (compared to the original)?

Is it possible to implement those features right now; or should we reengineer the project to make it easier to add the new features? The last question is rhetorical for this task, but you should think about it when doing a reengineering project. 
<br/>


Task 3: Visualization tool -- pacman-python
===================
The third task is to use our visualization tool of choice (CodeScene) to identify possible reengineering targets. Since we already had the "**First Contact**", now we should move to the "**Initial Understanding**" (OORP, p.83) of the system. One important reengineering pattern is to Study the "**Exceptional Entities**" (OORP, p.107).

Using CodeScene, can you identify artifacts that appear to be out of place? Could they benefit from refactoring activities? How is the complexity measurements for such artifacts compared to others?
<br/>

Task 4: Another Project -- django CMS
=============
Repeat the previous tasks using Django CMS project.

Discussions and Conclusion 
============
We have used metrics and visualization for the Initial Understanding, thereby demonstrating their 
potential support to the reengineering process.
 
Did the metrics and visualization tools used in this lab session provide you with the information 
you needed to fulfill the goals of the different Reengineering Patterns? Set up an argument about 
the issues concerning the use of such tools: when would you use them, when wouldn’t you? Can you 
envision other usages of these tools in other phases in the Reengineering Lifecycle?

Post-Lab Quiz: Metrics & Visualization
==========
Posted on WebCampus
