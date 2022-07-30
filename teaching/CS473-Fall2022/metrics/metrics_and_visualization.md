---
layout: page
title: Metrics and Visualization
permalink: /teaching/CS473-Fall2022/metrics/
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
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Reengineering Project" />
</form>

<br/>
<br/>

<p align="justify"/>

The purpose of these exercises is to stimulate discussion about the properties of a well-structured 
object-oriented design. This session is to provide you the first contact with tools in the lab. 
The tasks and assignments are designed to stimulate your comprehension of the topic and the tools. 
For Metrics and Visualization, consider the tools used in this session as the providers of data 
required to build up an argument for a system report or action plan. <br/>

Materials & Tools Used for this Session
========
* Lecture Sides [here]()
* [IntelliJ IDE](https://www.jetbrains.com/idea/) (you can use [Eclipse](https://www.eclipse.org/) at your discretion, but it may require some adaptations for the project we are using during the lab sessions)
* [JPacman](https://github.com/johnxu21/jpacman) repository.
* [CodeScene](https://codescene.com/) - **no** installation necessary, but it requires a GitHub account. This tool integration with GitHub allows it to visualize your repositories.
* [JsCity](https://github.com/ASERG-UFMG/JSCity/wiki/JSCITY) is an implementation of CodeCity to analyze JavaScript code.
<br/>


Auxiliary Tools
============
Auxiliary tools are not required for the lab session itself, but they may be useful to get additional information (or alternatives) on a project. Use them at your own discretion. 
* [Codecity](http://wettel.github.io/codecity.html) (only on Windows or Mac only possible on Linux after installing VisualWorks for Smalltalk). A preview of its functionalities can be found here.
* [Moose](http://moosetechnology.org/) provides a powerful platform for software analytics & measurements. 
* [Softwarenaut](http://scg.unibe.ch/softwarenaut) (only on Windows or Mac). This system does not require Eclipse. A preview of its functionalities can be found [here](https://vimeo.com/62767181). The tool can be download [here](http://scg.unibe.ch/download/softwarenaut/).
* [Eclipse Metrics](http://metrics2.sourceforge.net/). Old eclipse plugin to extract metrics. Interesting as a concept but severely outdated.

<br/>

Setup / Preparation
=============

First, make sure to fork the JPacman from the [Prof's repository](https://github.com/johnxu21/jpacman) into your GitHub account. It is necessary to fork the project because the free version of CodeScene can only see projects from your own account.


Second, go into CodeScene, and click on the "Login" menu (top-right corner). You can choose the option "Login with Github" at the bottom of that page. Once logged in, you can choose to create a new project, where CodeScene will show all the GitHub projects in your account. Select JPacman and go do the next part until it finishes (it might take a while, depending on the project). 


Download/Clone the JPacman project and open it on IntelliJ; build it. JPacman uses Gradle as a built/dependency manager. Make sure you can build and run it before doing any source code modification. Since this lecturer is all about visualization, we will not make any changes to the code. But you may need that on future lessons.


Also if have not already, download the book for this course "[Object-Oriented Reengineering Patterns](http://scg.unibe.ch/download/oorp/)" (Note: OORP, p.xx refers to a page in the pdf version of this book)
<br/>

Task 1: Introduction (React)
============
This first task has two goals: (i) to help familiarize yourself with the CodeScene interface; and (ii) to observe that not every visualization is useful for refactoring.

Visit the CodeScene website and click at the Showcases. These are examples (from a full version of CodeScene and not only the free version we are using) of projects analyzed by CodeScene. Select the React project.

Visit the JsCity website and look at the examples. You may want to select a simple example first to get acquainted. But after that, also select the "React" project to visualize (and be patient because it may take a while). 

What did you think of these visualization tools? Can you extract important information about the visualized project from them? Which visualization would be more useful to plan refactoring activities?
<br/>

Task 2: JPacman -- Hands-on
===============
For the second task, the goal is to start getting acquainted with the JPacman source code. Download/clone the repository and run the application. Now look at the source code and try to understand its internal structure. In the "docs/uml" folder there are two simplified UML diagrams.

As stated in the book (OORP, p.36), this is your "First Contact" with the software that needs reengineering activities. As often we ask ourselves "Where do I start?" (OORP, p.37).

Well, JPacman is a java implementation that is supposed to replicate the original [Pacman Game](https://en.wikipedia.org/wiki/Pac-Man). What features are missing in Jpacman (compared to the original)?

Is it possible to implement those features right now; or should we reengineer the project to make it easier to add the new features? The last question is rhetorical for this task, but you should think about it when doing a reengineering project. 
<br/>


Task 3: JPacman -- Visualization tool
===================
The third task is to use our visualization tool of choice (CodeScene) to identify possible reengineering targets. Since we already had the "First Contact", now we should move to the "Initial Understanding" (OORP, p.83) of the system. One important reengineering pattern is to Study the Exception Entities (OORP, p.107).

Using CodeScene, can you identify artifacts that appear to be out of place? Could they benefit from refactoring activities? How is the complexity measurements for such artifacts compared to others?
<br/>


Discussions and Conclusion 
============
We have used metrics and visualization for the Initial Understanding, thereby demonstrating their potential support to the reengineering process.
 
Did the metrics and visualization tools used in this lab session provide you with the information you needed to fulfill the goals of the different Reengineering Patterns? Set up an argument about the issues concerning the use of such tools: when would you use them, when wouldn’t you? Can you envision other usages of these tools in other phases in the Reengineering Lifecycle?
