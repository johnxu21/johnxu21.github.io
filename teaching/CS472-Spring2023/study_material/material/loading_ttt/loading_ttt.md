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

This text will show you in a few steps how to load the TicTacToe program (to be used in the Software Design and Development I) in CLion. 
The example starts from the first version TicTacToe10, but subsequent versions should load similarly.

**Goal:** 
The ultimate goal of this exercise is to set up the TicTacToe project in such a way that there are two configurations ("Build Configurations"): 
1.  a "Release" version in which it is only necessary for demonstration to the end user for acknowledgment; 
2.  We use a "Debug" version with extras during the development process (tests, debug, ...).

Step 1: Compile GTest
========
* The Google test framework must be compiled on the platform you are working on (MacOSX, Linux, Windows, ...). 
You do this by first downloading gtest [gtest-1.7.zip](https://drive.google.com/file/d/1TzuyNjnm92Zhkq89pHA7eP9SP9sbFa4C/view?usp=sharing). Decompress the zip file.
* Open a terminal and navigate to the gtest folder that you have unzipped
* Then run these commands to compile the framework:

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

[  7%] Building CXX object CMakeFiles/ttt.dir/TicTacToe.cpp.o
[ 14%] Building CXX object CMakeFiles/ttt.dir/TicTacToeMain.cpp.o
[ 21%] Linking CXX executable ttt
[ 21%] Built target ttt
[ 28%] Building CXX object _deps/googletest-build/googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
[ 35%] Linking CXX static library ../../../lib/libgtest.a
[ 35%] Built target gtest
[ 42%] Building CXX object CMakeFiles/ttt_debug.dir/TicTacToe.cpp.o
[ 50%] Building CXX object CMakeFiles/ttt_debug.dir/TicTacToeTests.cpp.o
[ 57%] Linking CXX executable ttt_debug
[ 57%] Built target ttt_debug
[ 64%] Building CXX object _deps/googletest-build/googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
[ 71%] Linking CXX static library ../../../lib/libgmock.a
[ 71%] Built target gmock
[ 78%] Building CXX object _deps/googletest-build/googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
[ 85%] Linking CXX static library ../../../lib/libgmock_main.a
[ 85%] Built target gmock_main
[ 92%] Building CXX object _deps/googletest-build/googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
[100%] Linking CXX static library ../../../lib/libgtest_main.a
[100%] Built target gtest_main
 
**** Build Finished ****
```

