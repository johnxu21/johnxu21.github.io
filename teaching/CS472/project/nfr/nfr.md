---
layout: page
title: Non-functional requirements
permalink: /teaching/CS472-Spring2023/project/nfr/
---

<form action="/teaching/CS472/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>
<form action="/teaching/CS472/study_material/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Study Material" />
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
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Project" />
</form>

<form id="main-form" action="/teaching/CS472/project/" method="post"></form>
<form id="sub-form1"  action="/teaching/CS472/project/FAQ"  method="post"></form>



<br/>
<br/>

In addition to the functional requirements specified by the customer, the customer also had several non-functional requirements that the project must meet. Each of these requirements was provided with a reason.

Required
=====
* **Platform**: The system must run on Linux and it must be programmed in C++. The system must 
compile with compiler flags ```-std=c++98``` and ```-Wall -Werror```. Use this CMakeLists.txt as an example.
* **Testing**: The customer expects a high-quality system, so there must be automatic tests. (Use the gtest library)
* **Contracts**: The customer expects a high-quality system, so there must be contracts in the system. 
(Use [DesignByContract.h](../../study_material/material/DesignByContract.h) for this)
* **Functionality**: The customer wants guarantees about the available functionality, so they must also be able to provide their input files.
* **Code Conventions**: Follow the C++ code conventions as specified in the [Program code box - student material](/teaching/CS472/study_material/).

