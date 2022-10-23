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

This text will show you in a few steps how to load the TicTacToe program (to be used in the Software Design and Development I) in ```CLion```. 
The example starts from the first version TicTacToe10, but subsequent versions should load similarly.

**Goal:** 
The ultimate goal of this exercise is to set up the TicTacToe project in such a way that there are two configurations ("Build Configurations"): 
1.  a ```release``` version in which it is only necessary for demonstration to the end user for acknowledgment; 
2.  We use a ```debug``` version with extras during the development process (```tests```, ```debug```, ...).

Step 1: Building GoogleTest with CMake
========
To build GoogleTest and your tests that use it, you need to tell your build system where to find its headers and source files.
The instructions for building googletest with ```cmake``` can be found on the googletest [README.md](https://github.com/google/googletest/tree/main/googletest) file.
Here we shall summarise a few points from the page. However, we encourage you to read the entire [README.md](https://github.com/google/googletest/tree/main/googletest) file.
You can either build ```googletest``` as a **standalone project** or it can be **incorporated into an existing CMake build for another project**.
Here we shall demonstrate the latter.

### Incorporating Into An Existing CMake Project
The trick is in editing the ```CMakeLists.txt``` and incorporate ```googletest``` into an existing project with ```cmake```.
Instruction on how to edit a ```CMakeLists.txt``` for a project can be found [here](https://www.jetbrains.com/help/clion/cmakelists-txt-file.html#cmakelist-template).

We shall use an example of a ```TicTacToe``` project version ```10```.
Unzip the project and import it in ``CLion``. When you look at the ```CMakeLists.txt``` file, you see that we have added the code snippet
we copied from the googletest [README.md](https://github.com/google/googletest/tree/main/googletest) file.


```cmake
# Incorporating Into An Existing CMake Project
# CMake to download GoogleTest as part of the build's configure step.
include(FetchContent)
FetchContent_Declare(
        googletest
        # Specify the commit you depend on and update it regularly. (latest googletest commit - October 19, 2022)
        URL https://github.com/google/googletest/archive/e07617d6c692a96e126f11f85c3e38e46b10b4d0.zip
)
# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)
```

Step 3 - Customize the CMakeLists
========

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

