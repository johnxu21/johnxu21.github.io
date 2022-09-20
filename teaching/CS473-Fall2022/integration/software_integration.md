---
layout: page
title: Software Integration
permalink: /teaching/CS473-Fall2022/integration/
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
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Software Integration" />
</form>
<form action="/teaching/CS473-Fall2022/dynamic/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
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

Version control systems (VCSs), which keep track of the software development history, have become an essential 
component of modern software development. With the increase of distributed software development, additional 
coordination tools and processes to facilitate collaboration between team members who may be working on different 
tasks have been introduced. For example, large software systems commonly make use of branching in distributed 
version control systems. Developers typically follow a branch-based development approach, where new features or bug 
fixes are developed in separate branches before being integrated into the master branch, or another stable branch

While branching (or forking where the developer may make a tracked copy of the work in a separate repository 
has several advantages such as allowing better separation of concerns and enabling parallel development
, it still comes at the cost of integration challenges. Once a developer has completed the intended work in a 
given branch, they need to merge their changes with the rest of the team’s work. At this point, merge conflicts 
may arise, because of inconsistent changes to the code. Previous studies have shown that up to 16% of merge 
scenarios lead to conflicts. Developers have to resolve such conflicts before proceeding, which wastes their 
time and distracts them from their main tasks.

Materials & Tools Used for this Session
========
* Lecture sides [here](../../../files/Integration.pdf)
* [IntelliJ IDE](https://www.jetbrains.com/idea/) (you can use [Eclipse](https://www.eclipse.org/) at your discretion, but it may require some adaptations for the project we are using during the lab sessions)
* [RefactoringsInMergeCommits](https://github.com/ualberta-smr/RefactoringsInMergeCommits) 
* [Refactoring-Aware Merging](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation)


Setup / Preparation
===============
In this lab you will play with two very related tools: [Refactorings in Merge Commits](https://github.com/ualberta-smr/RefactoringsInMergeCommits) and [Refactoring-Aware Merging](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation)

Task 1 - Refactorings in Merge Commits
============
In this task you will try to understand [Refactorings in Merge Commits](https://github.com/ualberta-smr/RefactoringsInMergeCommits)  analyzes merge commits in git repositries and determines whether refactoring changes are to blame for the conflicts.
Prepare the tool environment according to the system requirements of the tool located on the [README.md](https://github.com/ualberta-smr/RefactoringsInMergeCommits/blob/master/README.md) file. <br/>

Clone-and-own [RefactoringsInMergeCommits](https://github.com/ualberta-smr/RefactoringsInMergeCommits) and then open the project in  IntelliJ IDE.


**System Requirements** <br/>
* Linux or macOS
* git
* Java 11. If you have more than one Java version on your machine, you can run this command on the terminal inside Intellij **export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-11.0.14.jdk/Contents/Home**
* MySQL 5.7 (**Install this version of mysql**)
* I would recommend installing phpMyAdmin to help with running SQL queries. You can install it using **brew install --cask xampp** (if you have a Mac OS)


**Running the JAR file** <br/>

java -jar refactoring-analysis.jar <br/> <br/>
(You may have to run the commands **ln -sf /usr/share/zoneinfo/UTC /etc/localtime** to change the timezone to the local time)

Download the like [repList.txt](../../../files/repoList.txt) and replace it with of the default **reposList.txt** in the cloned project [RefactoringsInMergeCommits](https://github.com/ualberta-smr/RefactoringsInMergeCommits)

Task 1.2
===========
Scan through the code and understand how these different refactoring aware operations are implemented:
1. Detecting conflicting regions
2. Detecting evolutionary changes
3. Detecting refactorings
4. Detecting refactorings in the conflicting region

The above steps are explained in detail in **Section 3: Methodology** of the paper [Are Refactorings to Blame? An Empirical Study of Refactorings in Merge Conflicts](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8668012&tag=1). Of course reading the whole paper would be ideal, but reading only Section 3 should be sufficient.

You could also export the sql structure from the database and reverse engineer the ER diagram. Understand how the different tables are interconnected 

Task 1.2 - Optional
=================
Looking at the tool [Refactorings in Merge Commits](https://github.com/ualberta-smr/RefactoringsInMergeCommits) we can see that only a subset of the refactoring operations mentioned in the Readme.md of tool [RefactoringMiner](https://github.com/tsantalis/RefactoringMiner/tree/intellij-psi)
have been implemented. Extend [Refactorings in Merge Commits](https://github.com/ualberta-smr/RefactoringsInMergeCommits) with a set of more refactoring operations. Write and run tests to ensure that they have been well implemented.

**Note:** [Refactoring-Aware Merging](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation) implements refactoring operations of  [RefactoringMiner](https://github.com/tsantalis/RefactoringMiner/tree/intellij-psi) version 2.1.0. Some on the new refactorings are only present in later versions of the tool.

Task 2
======
[Refactoring-Aware Merging](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation) is a robust project comprising of two tools RefMerge and an Evaluation tool. 
 We are only interested [RefMerge](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation/tree/master/src/main/java/ca/ualberta/cs/smr/refmerge) that performs refactoring-aware merging operations.
[Refactoring-Aware Merging](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation) will be used in the final project, take time to understand how it is implemented. <br/>

## How to run
Follow the instruction on the [Readme.md file](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation) of the project to build and run the project.

1. **Clone and build RefactoringMiner** <br/>
Use **git clone https://github.com/tsantalis/RefactoringMiner.git** to clone RefactoringMiner. Then build 
RefactoringMiner with **./gradlew distzip**. It will be under build/distributions. <br/>
2. In order to use RefactoringMiner as a maven dependency in your project, you will need to **add RefactoringMiner to your local maven repository**
Add the following snippet to your project's build configuration file: <br/>
3. 
~~~ xml
<dependency>
  <groupId>com.github.tsantalis</groupId>
  <artifactId>refactoring-miner</artifactId>
  <version>2.1.0</version> 
</dependency>
~~~
 mvn install:install-file -Dfile=build/libs/RefactoringMiner-2.2.0.jar -DgroupId=com.github.tsantalis -DartifactId=refactoring-miner -Dversion=2.2.0 -Dpackaging=jar -DgeneratePom=false

3. Build the project
Click on build tab in the IntelliJ IDE and select Build Project to build RefMerge. <br/>

Task 2.1 - Optional
=================
Looking at the tool [RefMerge](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation/tree/master/src/main/java/ca/ualberta/cs/smr/refmerge) we can see that only a subset of the refactoring operations mentioned in the Readme.md of tool [RefactoringMiner](https://github.com/tsantalis/RefactoringMiner/tree/intellij-psi)
have been implemented. Extend [RefMerge](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation/tree/master/src/main/java/ca/ualberta/cs/smr/refmerge) with a set of more refactoring operations. Write and run tests to ensure that they have been well implemented.

**Note**: Although Task 2.1 is **optional** here. However, in the final report it is a **Required task**. Better to already do it and get acquainted.


Task 2.
==========
Scan through the code and understand how the following refactoring-aware operations are implemented (First Contact - Readall the Code in One Hour OORP, p.53).
1. Detect and Simplify Refactorings
2. Invert refactorings
3. Merge (In the [Project](/teaching/CS473-Fall2022/project/) the command **git merge** will be replaced with **git cherry-pick**)
4. Detect Refactoring Conflicts
5. Replay Refactorings

The above steps are described in detail in the paper: **Section 3 - REFMERGE: REFACTORING-AWARE OPERATION BASED MERGING** of the paper [A Systematic Comparison of Two Refactoring-aware Merging Techniques](https://arxiv.org/pdf/2112.10370.pdf)


