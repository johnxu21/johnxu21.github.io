---
layout: page
title: Frequently Asked Questions
permalink: /teaching/CS472-Spring2023/project/FAQ/
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
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="Groups" />
</form>
<form action="/teaching/CS472-Spring2023/project/FAQ/">
    <input type="submit" style="background-color:firebrick;float:left;color:white;width:130px;
height:30px;" value="FAQ" />
</form>
</div>

<br/>
<br/>

Frequently Asked Questions
=========

### General
* I have no idea how to find a partner.
  * During the first practical, try to ask around who is still without a group.
  * You may form a group of 10 (subject to motivation);
  * You may also (subject to motivation) deviate from the permitted group classification. But then it should be clear to everyone that the expertise in the duo is not entirely equal.
  * If you have not found a partner by Monday 23 January, please contact Prof. John Businge and the Graduate assistant by email. We will collect all the names of individuals who have not yet found anyone and then put you in touch with each other.

* Can we voluntarily choose a project? Do we all have the same project? 
  * No: it is an imposed project that changes every year. Within the project there are mandatory and optional parts so that you still have some freedom.
* Why can only the public attributes be used in the contracts?
  * A contract is part of the (public) interface of a class. Someone calling a method on a class must be able to verify that the pre and post conditions are met. This is only possible if a contract is limited to the public attributes. 
* I don't really understand the difference between ```Make``` and ```CMake```.
  * ```Make``` creates files based on "build-rules". But those "build rules" can be different depending on the platform on which you are creating the project. The ```include``` libraries are slightly different, the compiler flags are slightly different, .... To remedy that there is ```CMake```: that is a system that creates a ```Make``` file for the platform you are currently working on. So ```CMake``` is actually a meta level of ```Make```. 
  * See these links for more information: [CMake vs Make](https://prateekvjoshi.com/2014/02/01/cmake-vs-make/) and [CMake vs. Make](https://www.incredibuild.com/blog/cmake-vs-make).
* Can we also do the first practicals at home? Is it mandatory to come to the physical practicals? 
  * It is not mandatory to come to the physical practicals.
  * The first two practicals are for learning to work with (1) an XML parser and (2) tests and contracts. These exercises are not on point; they are just there to get you started with the software libraries you will need during the project. All the material is listed at the bottom of the [study material](/teaching/CS472-Spring2023/study_material/) tab. The assignments also contain a tutorial that you can follow step-by-step. So you can perfectly do the exercises from home in preparation for the project.
  * From the third practical it is free project work every week.
  * We like to physically organize the first three practicals because we can easily help with technical problems during the installation and use of the software libraries. Once the setup of your project is done, you can independently start the real programming.
* Should we study the three chapters? How does the theory exam work?
  * There is no separate exam for the theory. The final exam is a project defense and is similar to the interim project defenses. We'll go over your code and use the same criteria to evaluate.
* Is the project specification already online?
  * Yes
* Can we still come to the practicals every week?
  * Yes, the computer lab is available for you to work on the project together.
* Do we still get theory lessons?
  * No. The theory lessons are only during the first three weeks.
  * What if a group partner gives up?
  * Contact us as soon as possible. (By the way, this applies to all problems you might have with your partners) Then we look for an individual solution (adjusted planning, ...).

### About the Specification 1.0 (Traffic Simulation)
* What unit is the traffic light "cycle" and the vehicle generator "frequency"?
  * These are expressed in seconds. Note that each simulated second consists of several simulation steps. The simulation time (time in seconds that elapses during 1 simulation step) is equal to 0.0166. You can also find these in the table on the last page of the assignment.
* Will we still get XML files to test our project?
  * No, you will have to create XML files yourself to test your project.
* How should we simulate the traffic simulator automatically? Will this run indefinitely?
  * If you do not generate any trams, the simulation may stop when all vehicles have left the track. Otherwise, you are allowed to implement a maximum simulation time / maximum number of iterations.
* Is it true that trams never come to a complete stop? Is it true that trams that are behind another tram always slow down a little bit?
  * This is right! If this causes problems during testing, or with your contracts, you may round the acceleration, speed, and position to 3 decimal places. 

### About the Specification 2.0

