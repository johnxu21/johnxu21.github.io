---
layout: page
title: Study Material
permalink: /teaching/CS472-Spring2023/study_material/
---
<form action="/teaching/CS472-Spring2023/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>
<form action="/teaching/CS472-Spring2023/study_material/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
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

* Plan 1.0 [[PDF]()]  [[Excel]()] The project is done in groups of [X]; by the second week of class, you must have found a partner and let us know. A simple piece of paper with two names is sufficient, but here you will find an especially predestined form. Plan 1.0 must be issued during the second week.
* Timesheet 1.0 [PDF]()]  [[Excel]()] The time sheets for phase x must be submitted together with the planning for phase x + 1.
* Plan 2.0 [PDF]()]  [[Excel]()] In the second project planning you have to make a real choice from what you will or will not deliver in the end. You indicate that choice by means of Plan 2.0. Plan 2.0 must be issued the week after the first interim evaluation.
* Plan 2.1 [PDF]()]  [[Excel]()] You only have to submit Plan 2.1 if you want to change something compared to Plan 2.0. Then it must be handed in the week after the second interim evaluation. You must also argue there (using time sheets) why you want to adjust that planning.

Theory
=======
Copies of the slides and other materials used can be found here. 
* All in 1 bundle [PDF]()
* Sleeve [PDF]()
* Lesson 1 — Introduction + Reliability
  * Practical [PDF]()
  * Reliability [PDF]()
  * Wikipedia about "Mars Climate Orbiter"
  * Web-site for "5 Most Embarrassing Software Bugs in History"
* Lesson 2 - Adaptability
  * Adaptability [PDF]()
* Lesson 3 - Planning 
  * Planning [PDF]()

Program code
=====
References to some resources.
* The google test framework [gtest-1.7.zip](https://drive.google.com/file/d/1TzuyNjnm92Zhkq89pHA7eP9SP9sbFa4C/view?usp=sharing)
* Original can be found on [GitHub googletest](https://github.com/google/googletest)
* The test framework must also be compiled. This is done through ```cmake```. Instructions can be found at [GoogleTest Readme.md](https://github.com/google/googletest/blob/main/googletest/README.md)
* Design by contract [DesignByContract.h](material/DesignByContract.h) (A minimalist version with ```REQUIRE``` and ```ENSURE``` macros that -- if the condition is not met -- immediately stop the program with a simple message). 
* Loading [TicTacToe in CLion](material/loading_ttt/loading_ttt.md)
* A documentation generator [DoxyGen](https://doxygen.nl/) 

All sample code (both for theory and practicals) can be found below.
* TicTacToe version 1.0 [[zip](https://drive.google.com/file/d/1JjUfUbTjYL1WiENvwYu9XiOD1UvVGU6v/view?usp=sharing)] ("simplest that could possibly work" with unit tests and a counter that counts to 9)
* TicTacToe version 1.1 [[zip](https://drive.google.com/file/d/1JrPmkA79M_ciYxJA7qjx3D4HuAYv2d0J/view?usp=sharing)] (Basic version with game board filled alternately with X and O).
* TicTacToe version 1.2 [[zip](https://drive.google.com/file/d/1Jpt5lXoXR42aHVSYvQYRrs21MLx8V-ny/view?usp=sharing)] (Version with contracts and a first demonstration)
* TicTacToe version 1.3 [[zip](https://drive.google.com/file/d/1K0wAWi6cmORze6AA6nRbJ6EZirDrozec/view?usp=sharing)] (Version where the "magic numbers" are replaced by constants)
* TicTacToe version 1.4 [[zip](https://drive.google.com/file/d/1J9gDmBa1AFEC0-Q6Qe52kiBp_KwFMQ05/view?usp=sharing)] (Version where output is generated on a file; also tests with "CompareFiles")
* TicTacToe version 1.5 [[zip](https://drive.google.com/file/d/1Jp14EpX57pfigMokwlkeSeeSzJuc4YfX/view?usp=sharing)] (Version where a player is split off as a separate class)
* TicTacToe version 1.6 [[zip](https://drive.google.com/file/d/1JvBJ2uIiGn45Uxab08FBtT5eoKIYqNgG/view?usp=sharing)] (Version where players are assigned a series of moves)
* TicTacToe version 1.7 [[zip](https://drive.google.com/file/d/1JO5FqC0h07_a0cT4bSpwFlg39VyjAwn-/view?usp=sharing)] (Version in which the winner's information is tracked and calculated)
* TicTacToe version 1.8 [[zip](https://drive.google.com/file/d/1Jp1MlOeAGeO8odBRAVjMhS0cMuE5N-Wg/view?usp=sharing)] (Version in which the interface of the game board is adjusted (reset) for easier testing + customization scenarios)
* TicTacToe version 1.9 [[zip](https://drive.google.com/file/d/1J9xAF2yD-xTqAjS0IR_PgU4CkecaZhY4/view?usp=sharing)] (Version with early architecture: file manipulations are split off in TicTacToeUtils and the tests are split into DomainTests (for the domain layer) and OutputTests (for the output))
* TicTacToe version 2.0 [[zip](https://drive.google.com/file/d/1JqbsYLD58psG3BxGuFF15anr5VLQhk8N/view?usp=sharing)] (Version with an XML Importer that uses TinyXML to read XML files and populate a TicTacToeGame. Therefore, separate InputTests that process a series of XML files; some of them have errors and then the error messages are verified.)
* TicTacToe version 2.1 [[zip](https://drive.google.com/file/d/1JkV_GbIpwbv6YrtHnWNFda24OLE5t6dw/view?usp=sharing)] (Version with an exporter that exports a TicTacToeGame in various formats (ASCII, HTML). Therefore, separate OutputTests .)
* TicTacToe version 2.1 [[GitHub](https://github.com/johnxu21/TicTacToe_Git)] (Same version 2.1, but now published on GitHub. You can fork this project and work on it like that]

Practicals
========

## Week 1: 
The practical during the 1st week deals with the xml parser, a mandatory component of the project. All materials can be found below.
* [Tasks](../../../files/472Files/Week1-Tasks.pdf)
* [eenCD.xml](material/eenCD.xml), [cdCatalog.xml](material/cdCatalog.xml), [eenCDError.xml](material/eenCDError.xml), [cdCatalogError.xml](material/cdCatalogError.xml)
* [Possible solution](https://drive.google.com/file/d/1XLZDTpHjaxZ4RmlUlU0ic58ngIAz3d3m/view?usp=sharing)

## Week 2: 
The lab during the 2nd week deals with unit tests, debugging and contracts. All supplies can be found below.
* [Tasks](../../../files/472Files/Week1-Tasks.pdf)
* [CMakeLists.txt](material/CMakeLists.txt)
* [Fighterplane.cpp](material/Fighterplane.cpp), [Exceptions.h](material/Exceptions.h), [Largest.cpp](material/Largest.cpp)
* The google test framework [[gtest-1.7.zip](https://drive.google.com/file/d/1TzuyNjnm92Zhkq89pHA7eP9SP9sbFa4C/view?usp=sharing)]
* Newer versions of google test can be found on  [[Github-googletest](https://github.com/google/googletest/releases)]
* The test framework must also be compiled. Use the instructions to load TicTacToe in CLion as an example [[load-tictactoe-clion](material/loading_ttt/loading_ttt.md)]
















