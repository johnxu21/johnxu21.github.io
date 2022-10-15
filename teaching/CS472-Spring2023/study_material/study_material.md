---
layout: page
title: Study Material
permalink: /teaching/CS472-Spring2023/
---
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
<form action="/teaching/CS472-Spring2023/Project/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Project" />
</form>


<br/>
<br/>

All study material to support theory as well as practicals is collected here.

Project progress
============
Allowed grouping [PDF]() You can freely choose your partner, with the restriction that it 
depends on your results for "Introduction to Programming". A list of the allowed groups 
will be published here during the *first* week.

During the semester you have to keep us informed of the state of affairs. A number of forms are provided for this. In all forms you must adjust all boxes with a (*) and all columns with a (+).

* Plan 1.0 [ [PDF]() | [Excel]() ] The project is done in groups of [X]; by the second week of class, you must have found a partner and let us know. A simple piece of paper with two names is sufficient, but here you will find an especially predestined form. Plan 1.0 must be issued during the second week.
* Timesheet 1.0 [ [PDF]() | [Excel]() ] The time sheets for phase x must be submitted together with the planning for phase x + 1.
* Plan 2.0 [ [PDF]() | [Excel]() ] In the second project planning you have to make a real choice from what you will or will not deliver in the end. You indicate that choice by means of Plan 2.0. Plan 2.0 must be issued the week after the first interim evaluation.
* Plan 2.1 [ [PDF]() | [Excel]() ] You only have to submit Plan 2.1 if you want to change something compared to Plan 2.0. Then it must be handed in the week after the second interim evaluation. You must also argue there (using time sheets) why you want to adjust that planning.

Theory
=======
Copies of the slides and other materials used can be found here. 
* All in 1 bundle [ PDF ]
* Sleeve [ PDF ]
* Lesson 1 — Introduction + Reliability
  * Practical [ PDF ]
  * Reliability [ PDF ]
  * Wikipedia about "Mars Climate Orbiter"
  * Web-site for "5 Most Embarrassing Software Bugs in History"
* Lesson 2 - Adaptability
  * Adaptability [pdf]()
* Lesson 3 - Planning 
  * Planning [pdf]()

Source code
=====
References to some resources.
* The google test framework [ gtest-1.7.zip | gtest-1.6.zip ]
* Original can be found on [GitHub googletest](https://github.com/google/googletest)
* The test framework must also be compiled. This is done through cmake. Instructions can be found at [GoogleTest Readme.md](https://github.com/google/googletest/blob/main/googletest/README.md)
* Design by contract [DesignByContract.h](material/DesignByContract.h) (A minimalist version with REQUIRE and ENSURE macros that -- if the condition is not met -- immediately stop the program with a simple message). 
* Loading [TicTacToe in CLion](loading_TicTacToe_in_CLion.md)
* A documentation generator [DoxyGen](https://doxygen.nl/) 

All sample code (both for theory and practicals) can be found below.
* TicTacToe version 1.0 [zip]() ("simplest that could possibly work" with unit tests and a counter that counts to 9)
* TicTacToe version 1.1 [zip]() (Basic version with game board filled alternately with X and O).
* TicTacToe version 1.2 [zip]() (Version with contracts and a first demonstration)
* TicTacToe version 1.3 [zip]() (Version where the "magic numbers" are replaced by constants)
* TicTacToe version 1.4 [zip]() (Version where output is generated on a file; also tests with "CompareFiles")
* TicTacToe version 1.5 [zip]() (Version where a player is split off as a separate class)
* TicTacToe version 1.6 [zip]() (Version where players are assigned a series of moves)
* TicTacToe version 1.7 [zip]() (Version in which the winner's information is tracked and calculated)
* TicTacToe version 1.8 [zip]()
* TicTacToe version 1.9 [zip]()
* TicTacToe version 2.0 [zip]() (Version with an XML Importer that uses TinyXML to read XML files and populate a TicTacToeGame. Therefore, separate InputTests that process a series of XML files; some of them have errors and then the error messages are verified.)
* TicTacToe version 2.1 [zip]() (Version with an exporter that exports a TicTacToeGame in various formats (ASCII, HTML). Therefore, separate OutputTests .)
* TicTacToe version 2.1 [zip]() (Same version 2.1, but now published on github. You can fork this project and work on it like that]

Practicals
========

* Week 1: The practical during the 1st week deals with the xml parser, a mandatory component of the project. All materials can be found below.















