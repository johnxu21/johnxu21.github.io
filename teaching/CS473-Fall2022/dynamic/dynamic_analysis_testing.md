---
layout: page
title: Dynamic Analysis- Testing
permalink: /teaching/CS473-Fall2022/dynamic/
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
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
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

Dynamic analysis is “the analysis of the properties of a running software system” 
[[Ball1999](https://ansymore.uantwerpen.be/system/files/Ball1999.pdf)]. 
It is complementary to static analysis techniques. Some properties that cannot be 
studied through static analysis can be examined with dynamic analysis and vice versa. 
The applications of dynamic analysis techniques are very broad: program comprehension, 
system verification, resource profiling, test analysis, etc. In this session, we focus on 
one very important aspect of dynamic analysis: Testing.

As the chapter so eloquently states, "Tests: Your Life Insurance!" (OORP, p.149). 
Tests are essential for Reengineering activities. They can help you: (1) to reveal unwanted 
side effects of refactoring ("Write Tests to Enable Evolution", OORP, p.153); and (2) to 
understand the inner workings of a system ("Write tests to Understand", OORP, p.179). 

The presence of automated tests does however not offer any guarantee about its quality. 
Do the tests cover the whole system or are some parts left untested? 
Which parts are covered to which extend? Hence, measuring test coverage is a useful, even 
necessary, way to assess the quality and usefulness of a test suite in the context of reengineering.

Materials & Tools Used for this Session
===============

* Session slides [here]().
* [IntelliJ IDE](https://www.jetbrains.com/idea/) (you can use [Eclipse](https://www.eclipse.org/) at your discretion, but it may require some adaptations for the project we are using during the lab sessions)
* [JPacman](https://github.com/johnxu21/jpacman) repository.
* [SonarQube](https://www.sonarqube.org/) is a tool/platform that performs static analysis on source codes. Download the free community edition. 
* [LittleDarwin](https://github.com/aliparsai/LittleDarwin) is a tool to perform Mutation testing on Java applications. Mutation testing is a relatively new topic, therefore it is difficult to find working tools for it. 
* [JaCoCo](https://www.jacoco.org/jacoco/index.html) is an eclipse plugin for coverage analysis. It is also available as a maven repository. Newer versions of IntelliJ already have this plugin pre-installed as a part of the test coverage plugin.
* [Pitest](http://pitest.org/) and [Pitest Repo](https://github.com/hcoles/pitest) is a state of the art mutation testing system, providing gold standard test coverage for Java and the jvm. It's fast, scalable and integrates with modern test and build tooling.

Auxiliary Tools
============
Auxiliary tools are not required for the lab session itself, but they may be useful to get additional 
information (or alternatives) on a project. Use them at your own discretion. 

* [DSpot](https://github.com/STAMP-project/dspot) is a tool for test-amplification in Java code. 
Test-amplification generates new test cases using the original tests as seeds. It supports projects 
* build in Maven and Gradle, and it has plugins for IntelliJ and Eclipse.
* [Randoop](https://randoop.github.io/randoop/) is a test generation tool. It automatically generates unit tests for Java classes.

Setup / Preparation
==============
Be sure to follow the setup and the tasks from the lab [Refactoring Assistants](/teaching/CS473-Fall2022/refactoring/). 
Especially, the task on executing ```SonarQube```. You will also need [IntelliJ IDE](https://www.jetbrains.com/idea/) and ```JPacman```. 
Moreover, if you have not already, download the book for this course "Object-Oriented Reengineering Patterns

Get/Install the tools & plugins detailed in the Materials above (not the auxiliary tools, they are optional 
and will not be used in this lab session).


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
for your test case. The hardest part is instantiating a ```Player``` object as it requires other objects. 
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

Task 4 -- SonarQube Coverage Information on JPacman
======================
 
```SonarQube``` is a static analysis tool. But it can show the results from test coverage in its interface. 
First, let's run ```SonarQube``` as is (note that you need to have Java JDK 11 to run the current version of 
SonarQube). Make sure your SonarQube service is running. Open your browser in ```localhost:9000``` and if you 
can see the SonarQube page, it is running. If not you should check the 
[SonarQube documentation](https://docs.sonarqube.org/latest/setup/get-started-2-minutes/) on how to start the 
service or the lab session on [Refactoring Assistants](/teaching/CS473-Fall2022/refactoring/). 
 
You should see your ```JPacman``` project on ```SonarQube```. Click on the tab ```Measures``` and on the left 
menu select ```Coverage``` > ```Overview```. You can see that SonarQube has no coverage information. 
Click on ```Unit tests``` on the left submenu, and you will not see your new ```PlayerTest``` is in here. 
That is because we added this test after ```SonarQube``` performed its last analysis.
Let's update it by running the following command on ```IntelliJ terminal``` (**all in the same line**):
```
./gradlew sonarqube -Dsonar.projectKey=jpacman -Dsonar.login=admin -Dsonar.password=reengineering
```

You can also use the token instead of ```login/password``` if you prefer. Now go back to the ```SonarQube``` 
page and look over the new information added for JPacman. Even though ```SonarQube``` does not perform 
dynamic analysis and cannot execute your tests, it does automatically fetch coverage information from your 
```JaCoCo``` XML report.
 
Since the ```JPacman``` on the course repository is already configured to output ```XML``` reports for 
```JaCoCo```, you are fine. However, if you do want to configure that on other projects, make sure to change 
```build.gradle file```. Inside that file search for ```jacocoTestReport``` and add ```xml.enabled true``` 
inside the ```reports``` group. You can see an example on the JPacman ```gradle.build``` lines 62-68. 
To be sure, check the folder ```build/reports/jacoco/test```, there should be a file there named 
```jacocoTestReport.xml```. If the xml file is not there, try to do a ```./gradlew build```, look for errors, 
and finally another run with coverage. 
 
To reiterate, your ```SonarQube``` should automatically fetch the ```JaCoCo XML``` report and show you 
coverage information after performing another analysis with the above command. If you have that, you can 
jump to the next paragraph. In case your SonarQube is still not showing coverage even after the ```JaCoCo XML```
report, you may need to inform SonarQube by the command line where the report is located. 
This is the command for that (run on IntelliJ terminal -- **all in the same line**):
```
./gradlew sonarqube -Dsonar.projectKey=jpacman -Dsonar.login=admin -Dsonar.password=reengineering -Dsonar.coverage.jacoco.xmlReportPath=build/reports/jacoco/test/html/jacocoTestReport.xml
```
Check SonarQube page again (localhost:9000) and try to see the coverage overview. Then, click on the 
"**Conditions to Cover**" (Branches) and select the ```Player``` file. Check this visualization option which 
is very similar to JaCoCo but more interactive. 
 
**Questions:**
* What do you think of the overview coverage visualization provided by SonarQube?
* Which did you find better to visualize the source code with branch coverage: JaCoCo or SonarQube?

Task 5 -- Mutation Testing on JPacman
=============
 
Mutation testing is a method of determining the quality of a test suite in detail. Mutation testing simulates 
faults and checks whether the test suite is good enough to catch those simulated faults. It is performed by 
injecting faults into the software and counting the number of these faults that make at least one test fail. 
The process for mutation testing requires the following steps. First, faulty versions of the software are created 
by introducing a single fault into the system (Mutation). This is done by applying a known transformation 
(Mutation Operator) on a certain part of the code. After generating the faulty versions of the software (Mutants), 
the test suite is executed on each one of these mutants. If there is an error or failure during the execution of 
the test suite, the mutant is marked as killed (Killed Mutant). On the other hand, if all tests pass, it means 
that the test suite could not catch the fault and the mutant has survived (Survived Mutant). Mutation testing 
demands a green test suite — a test suite in which all the tests pass — to run correctly. The final result is 
calculated by dividing the number of killed mutants by the number of all mutants. A test suite is said to achieve 
full test adequacy whenever it can kill all of the mutants. Such test suites are called mutation-adequate test suites. 
 
For the lab, we recommend using the tool [LittleDarwin](https://github.com/aliparsai/LittleDarwin) to perform 
mutation testing on Java. This tool was developed, at the [University of Antwerp](https://www.uantwerpen.be/en/). 
[LittleDarwin](https://github.com/aliparsai/LittleDarwin) is a mutation testing tool written in python that can 
analyze a wide range of Java applications. It is built with the purpose of easy deployment in an industrial 
environment, and it can handle complicated build system structures often found in such cases.  
 
To install LittleDarwin follow the instructions on its GitHub page. On Mac/Linux already with python you 
just need to use the following command to install it:
```
pip3 install littledarwin
```

In this task, you will try mutation testing on JPacman. Install LittleDarwin and run it on JPacman source code. 
Mutation testing is a slow procedure, the process may take between 10 and 25 minutes on JPacman. Therefore, 
don't "kill" the process if you think it is taking too long (let the tool do its job). Also, make sure to run 
LittleDarwin in a separate terminal/command window (otherwise you may freeze your IntelliJ). 
Use the following command inside the jpacman folder:
```
littledarwin  -m -b  -p ./src/main/ -t ./ -c ./gradlew,test --timeout=180
```
After it is finished, you can find the report in a structure similar to ```/LittleDarwinResults/report.html``` 
(there is a zip in the repository with such reports for JPacman so that you can see the results without waiting). 
This is like a JaCoCo report but instead of showing coverage percentage, it shows Mutation Coverage (
i.e., the percentage of mutants killed). A high mutation score indicates that your test suite is a good quality one. 
Take the JaCoCo report or SonarQube results on coverage and compare it with the mutation coverage.
 
**Questions:**
* Find classes that have low mutation coverage and high statement coverage. What does this indicate?
* In these classes, find a survived mutant that is within a covered statement (you can use the line numbers and the before-after comments inside each mutant to find them in the code). Why does this happen? 
* Find classes that have high mutation coverage and low statement coverage. What does this indicate?
* In these classes, look for a killed mutant that is not within a covered statement. Why does this happen?
* Given the previous observations, do you think statement coverage is a reliable metric for the quality of the test suite? Why (not)?
* Can the accuracy of mutation testing be improved? If yes, how do you think it is possible?
* How can mutation testing help write new tests?
 
 
Optional Task -- Increasing (Even More) the Coverage on JPacman
================
 
As an optional task, try to increase the coverage even further on JPacman. Look for places with lower coverage and 
create new tests for those. This could help you understand better the application as explained in the pattern 
"Write tests to Understand" (OORP, p.179). 
 
**Questions:**
* Did your knowledge of JPacman inner structures improve after creating new tests for it?
* Do you feel more confident in changing the artifacts where you increased their coverage?

