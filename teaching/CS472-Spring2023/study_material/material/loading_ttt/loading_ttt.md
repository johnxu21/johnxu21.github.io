---
layout: page
title: CS472 - Loading TicTacToe in CLion
permalink: /teaching/CS472-Spring2023/study_material/loading_ttt/
---

<form action="/teaching/CS472-Spring2023">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>
<form action="/teaching/CS472-Spring2023/study_material">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Study Material" />
</form>
<form action="/teaching/CS472-Spring2023/Timetable">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Timetable" />
</form>
<form action="/teaching/CS472-Spring2023/Exam">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Exam" />
</form>
<form action="/teaching/CS472-Spring2023/project">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Project" />
</form>


<br/>
<br/>

This text will show you in a few steps how to load the TicTacToe program (to be used in the Project Software Engineering) in CLion. The example starts from the first version TicTacToe10, but subsequent versions should load similarly.

**Goal:** 
The ultimate goal of this exercise is to set up the TicTacToe project in such a way that there are two configurations ("Build Configurations"): 
1.  a "Release" version in which only the most necessary for a demonstration to the acknowledgment of the end user ; 
2.  We use a "Debug" version with extras during the development process (tests, debug, ...).

Step 1: Compile GTest
========
* The google test framework must be compiled on the platform you are working on (MacOSX, Linux, Windows, ...). 
You do this by first downloading gtest [gtest-1.7.zip](https://drive.google.com/file/d/1TzuyNjnm92Zhkq89pHA7eP9SP9sbFa4C/view?usp=sharing). Decompress the zip file.
* Open a terminal and navigate to the gtest folder that you have unzipped
* *Then run these commands to compile the framework:

```commandline
./configure
cmake .
make 
```

* This causes the libraries ```libgtest.a``` and ```libgtest_main.a``` to be created. These are the files we need for our project and the ```include``` folder.

Step 2: Add the GTest files to the project
===========
* In your project, create a new folder called ```gtest```. Create another folder in it called ```lib```.
* Copy the libraries ```libgtest.a``` and ```libgtest_main.a``` to the directory ```gtest/lib```.
* Copy the ```include``` folder to the ```gtest``` folder.
* In the end we should get this folder structure:

```
./gtest:
include
lib

./gtest/include:
gtest

./gtest/include/gtest:

.
gtest.h
.

./gtest/lib:
libgtest.a
libgtest_main.a
```

* Make sure you have an unzipped version of a TicTacToe ```zip``` or ```tar``` file already. 
In the example, we have extracted version 10, much like the one below, but in later versions, 
there will be more files extracted.

```commandline
./src:
TicTacToe.cpp
TicTacToe.h
TicTacToeMain.cpp
TicTacToeTests.cpp
```

Step 3 - Customize the CMakeLists
========
* Once all the files are in the right place, all we need to do is edit the CMakeLists.txt. You can download it here:
* [CMakeLists.txt](../CMakeLists.txt)
* Using this ```CMakeLists.txt```, ```CLion``` will automatically create two run configurations: a ```'ttt'``` which builds and executes the Release version, and a ```'ttt_debug'``` which builds and executes the Debug version.

Step 4 - Test and Demonstration run
========
* First we build the Debug configuration. 
* The build process should be seamless and the console should show something like the following.

```commandline
**** Build of configuration Debug for project TicTacToe ****

make all 
Building file: ../src/TicTacToe.cpp
Invoking: GCC C++ Compiler
g++ -I../../../workspace/gtest/include -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/TicTacToe.d" -MT"src/TicTacToe.d" -o "src/TicTacToe.o" "../src/TicTacToe.cpp"
Finished building: ../src/TicTacToe.cpp
 
Building file: ../src/TicTacToeTests.cpp
Invoking: GCC C++ Compiler
g++ -I../../../workspace/gtest/include -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/TicTacToeTests.d" -MT"src/TicTacToeTests.d" -o "src/TicTacToeTests.o" "../src/TicTacToeTests.cpp"
Finished building: ../src/TicTacToeTests.cpp
 
Building target: TicTacToe
Invoking: MacOS X C++ Linker
g++ -L../../../workspace/gtest/lib -o "TicTacToe"  ./src/TicTacToe.o ./src/TicTacToeTests.o   -lgtest -lgtest_main
Finished building target: TicTacToe
 

**** Build Finished ****
```

