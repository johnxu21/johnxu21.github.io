---
layout: page
title: CS472 - Loading TicTacToe in CLion
permalink: /teaching/CS472-Spring2023/
---

This text will show you in a few steps how to load the TicTacToe program (to be used in the Project Software Engineering) in CLion. The example starts from the first version TicTacToe10, but subsequent versions should load similarly.

**Goal:** 
The ultimate goal of this exercise is to set up the TicTacToe project in such a way that there are two configurations ("Build Configurations"): 
1.  a "Release" version in which only the most necessary for a demonstration to the acknowledgment of the end user ; 
2.  We use a "Debug" version with extras during the development process (tests, debug, ...).

Step 1: Compile GTest
========
* The google test framework must be compiled on the platform you are working on (MacOSX, Linux, Windows, ...). You do this by first downloading gtest [gtest-1.7.zip](https://drive.google.com/file/d/1TzuyNjnm92Zhkq89pHA7eP9SP9sbFa4C/view?usp=sharing). Decompress the zip file.
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
* Copy the include folder to the ```gtest``` folder.
* In the end we should get this folder structure:

```commandline
./gtest:
include
lib

./gtest/include:
gtest

./gtest/include/gtest:
...
gtest.h
...

./gtest/lib:
libgtest.a
libgtest_main.a
```

* Make sure you have an unzipped version of a ```TicTacToe``` ```zip``` or ```tar``` file already. In the example, we have extracted version 10, much like the one below, but in later versions, there will be more files extracted.
```commandline
./src:
TicTacToe.cpp
TicTacToe.h
TicTacToeMain.cpp
TicTacToeTests.cpp
```

