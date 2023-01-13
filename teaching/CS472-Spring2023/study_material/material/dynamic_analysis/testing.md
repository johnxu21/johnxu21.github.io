---
layout: page
title: CS472 - Dynamic Analysis
permalink: /teaching/CS472-Spring2023/study_material/dynamic_analysis/
---

Dynamic analysis is “the analysis of the properties of a running software system” 
[[Ball1999](https://ansymore.uantwerpen.be/system/files/Ball1999.pdf)]. 
It is complementary to static analysis techniques. Some properties that cannot be 
studied through static analysis can be examined with dynamic analysis and vice versa. 
The applications of dynamic analysis techniques are very broad: program comprehension, 
system verification, resource profiling, test analysis, etc. In this session, we focus on 
one very important aspect of dynamic analysis: Testing.

"Tests: Your Life Insurance!" 
Tests are essential for software engineering activities. They can help you: 
1. to reveal unwanted side effects of refactoring 
2. to understand the inner workings of a system.


The presence of automated tests does however not offer any guarantee about its quality. 
Do the tests cover the whole system or are some parts left untested? 
Which parts are covered to which extent? Hence, measuring test coverage is a useful, even 
necessary, way to assess the quality and usefulness of a test suite in the context of software engineering.

Materials & Tools Used for this Session
===============

* Session slides [here](../../../files/Testing.pdf).
* [IntelliJ IDE](https://www.jetbrains.com/idea/) (you can use [Eclipse](https://www.eclipse.org/) at your discretion, but it may require some adaptations for the project we are using during the lab sessions)
* [JPacman](https://github.com/johnxu21/jpacman) repository.
* [JaCoCo](https://www.jacoco.org/jacoco/index.html) is an eclipse plugin for coverage analysis. It is also available as a maven repository. Newer versions of IntelliJ already have this plugin pre-installed as a part of the test coverage plugin.


Setup / Preparation
=============

First, make sure to fork the JPacman from the [Prof's repository](https://github.com/johnxu21/jpacman) into your GitHub account. It is necessary to fork the project because the free version of CodeScene can only see projects from your own account.

To start getting acquainted with the JPacman source code. Download/Clone the JPacman project and open it on IntelliJ; build it. JPacman uses Gradle as a built/dependency manager. Make sure you can build and run it before doing any source code modification.
Now look at the source code and try to understand its internal structure. In the "docs/uml" folder there are two simplified UML diagrams.

Task 1 -- JPacman Test Coverage
===========
 
We will begin by using the [IntelliJ IDE](https://www.jetbrains.com/idea/) test coverage plugin. 
The testing and coverage plugins should be enabled by default. If you are not sure, check under ```IntelliJ IDEA > Preferences > Plugins > installed``` if your 
plugins called ```Code Coverage for Java```, ```JUnit```, and ```TestNG``` are enabled.
 
First, make sure that you can test your JPacman, by using the following command line in the 
[IntelliJ IDE](https://www.jetbrains.com/idea/) terminal:
```
./gradlew test
```
**Note:** Remember to set the project to point to the JDK version on which it was built. Look at ```External Libraries``` under the 
Project's folder in IntelliJ IDE to see the JDK version.

Now, right-click on the ```test``` folder (inside the ```src``` folder) and select the option "Run 'Tests' 
in ```jpacman.test``` with Coverage". If that option is not available, select "Build Module 
```jpacman.test```" and after the build right-click again and the option  "Run 'Tests' in 
```jpacman.test``` with Coverage" should be available.

Alternatively, you can also right-click on the Gradle task ```test```, inside the module ```Task->verification```
shown in the ```Gradle plugin``` (default position is a collapsed tab on the right part of your IntelliJ). 
Select ```Run 'jpacman [test]' with Coverage```. This Gradle task should produce the same coverage. 
Therefore, use whichever you prefer. 
 
If everything executed without errors, you should see a new window showing the code coverage. 
Please try to remember this coverage (or take a screenshot to not depend on your memory).
 
**Questions:**
* Is the coverage good enough?
* If you make any changes in ```JPacman``` sources, can you rely on the current tests to catch faults?

Task 2 -- Increasing Coverage on JPacman
===================
  
For the second task, we will increase the coverage on JPacman. Doing that is very simple, 
we just need to write more tests. In this task, we are going to write one new test case. 
As you have seen from **Task 1** that the coverage for several packages is zero percent.
 
    Let's create a simple ```unit test``` on a method. We will test the ```isAlive()``` method in class ```Player``` 
(package ```level```). You should look at the ```DirectionTest``` class (folder ```test```, package ```board```) as a template 
for your test case. **The hardest part is instantiating a ```Player``` object as it requires other objects.** 
The ```PlayerFactory``` class is responsible for creating instances of ```Player```. And, ```PlayerFactory``` 
constructor requires a ```PacManSprites``` (package ```sprites```) object. Therefore, you need to instantiate a 
```PacManSprites``` object, to pass it on to the constructor of ```PlayerFactory```, and only then you can 
call the factory method to create a ```Player```.
 
Create the package ```level``` in the ```test``` folder. Then, create the class ```PlayerTest``` inside this 
package ```level```. Now you can write the test case for testing the method ```isAlive()``` from ```Player```. 
 
[Here is an example](/teaching/CS473-Fall2022/dynamic/PlayerTest.java_.txt) of such a test class, but I 
strongly advise you to try for yourself (it is a simple test and the hardest part is just to instantiate 
the objects).
 
After adding the new test, build ```jpacman.test``` again and run it with coverage. If your test does not 
have any errors, you should see the IntelliJ window showing the code coverage. Leave this window with the 
coverage information on as you may need it to answer the questions from the next task 
(or take a screenshot of it).
 
**Questions:**
* How did the new test affect the coverage?
* Do you think 100% coverage is feasible?
* What would you propose as a good level of code coverage?
 
 
Task 3 -- JaCoCo Report on JPacman
===============

The gradle build file provided in ```JPacman```, already has ```JaCoCo``` configured. Look at the folder 
```build/reports/jacoco/test/html```, right-click on the file ```index.html``` and select 
"Open in Browser". This is the coverage report from the ```JaCoCo``` tool. As you can see, ```JaCoCo``` shows not only 
line coverage but also branch coverage. Click on the ```level``` package, then on the ```Player``` class, 
and after that on any method. You will see the source code with color information on which branches are 
covered (or partially covered).
 
**Questions:**
* Are the coverage results from JaCoCo similar to the ones you got from IntelliJ in the last task? Why so or why not?
* Did you find helpful the source code visualization from ```JaCoCo``` on uncovered branches?
* Which visualization did you prefer, IntelliJ coverage window or ```JaCoCo``` report?
