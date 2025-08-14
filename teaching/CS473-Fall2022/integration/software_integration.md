---
layout: page
title: Software Integration
permalink: /teaching/Software-Reengineering/integration/
---

<form action="/teaching/Software-Reengineering/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>
<form action="/teaching/Software-Reengineering/metrics/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Metrics and Visualization" />
</form>
<form action="/teaching/Software-Reengineering/refactoring/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Refactoring Assistants" />
</form>
<form action="/teaching/Software-Reengineering/dynamic/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Dynamic Analysis: Testing" />
</form>
<form action="/teaching/Software-Reengineering/integration/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Software Integration" />
</form>
<form action="/teaching/Software-Reengineering/msr/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Mining Software Repositories" />
</form>
<form action="/teaching/Software-Reengineering/project/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Reengineering Project" />
</form>

<br/>
<br/>

In this session, we will explore tools that assist in software integration across related but 
independently evolving repositories. Many software variants (forks that share a common origin) fail to 
reuse relevant bug fixes or enhancements from each other. Prior work with **PaReco**
([paper](https://dl.acm.org/doi/10.1145/3540250.3549112)) shows that reuse gaps often appear as missed 
opportunities (patch present in the source but absent in the target) or effort duplication (similar patch 
re‑implemented manually). Our extended tool, **GACPD**, builds on **PaReco** with broader language support, 
faster token normalization, and developer-facing outputs to surface **candidate patches** worth reusing. 
When selecting what to integrate, apply **Most Valuable First** (OORP, p.29) to prioritize the highest‑impact 
patches, and **Keep It Simple** (OORP, p.37) to avoid unnecessary complexity in your plan.

Despite automated detection, structural divergence caused by refactorings (renames, moves, interface 
changes) can block direct reuse. **RePatch** ([paper](https://arxiv.org/pdf/2508.06718)) performs 
**refactoring‑aware patch integration** by aligning the source and target around detected refactorings, 
applying the patch, then replaying those refactorings so the target keeps its structure. Guard your work 
with **Tests: Your Life Insurance** (OORP, p.149), use **Write Tests to Understand** (OORP, p.179) when 
behavior is unclear, and **Grow Your Test Base Incrementally** (OORP, p.159) to expand coverage only where 
the integration touches. Keep adaptations minimal (again, **Keep It Simple**, p.37), focus on the immediate 
collaborators of the change, and document any manual decisions for review.


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
In this task you will try to understand how [Refactorings in Merge Commits](https://github.com/ualberta-smr/RefactoringsInMergeCommits)  analyzes merge commits in git repositries and determines whether refactoring changes are to blame for the conflicts.
Prepare the tool environment according to the system requirements of the tool located on the [README.md](https://github.com/ualberta-smr/RefactoringsInMergeCommits/blob/master/README.md) file. <br/>

**You may also follow the instructions below that are adapted from [README.md](https://github.com/ualberta-smr/RefactoringsInMergeCommits/blob/master/README.md).** <br/>

**System Requirements** <br/>
* Linux or macOS
* git
* Java 11. If you have more than one Java version on your machine, you can run this command on the terminal inside Intellij 
```
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-11.0.14.jdk/Contents/Home
```
* MySQL 5.7 (**Install this version of mysql**). Create a ```USERNAME``` and ```PASSWORD```, they are needed in the next step.
* I would recommend installing phpMyAdmin to help with running SQL queries. You can install it using **brew install --cask xampp** (if you have a Mac OS)



**Running the JAR file** <br/>

* You need to start MySql server. You can do this by starting ```xammp``` (if you are using a Mac OS, just go to the xampp application (folder) and double-click the file ```manager-osx```)
* When mysql server is up and running, type this in the browser to confirm that everything is working fine  ```http://localhost/phpmyadmin/index.php```
* Clone-and-own [RefactoringsInMergeCommits](https://github.com/ualberta-smr/RefactoringsInMergeCommits) and then open the project in  IntelliJ IDE.
* Edit the ```database.properties``` file and replace the ```USERNAME``` and ```PASSWORD``` with the ones you created for ```mysql``` earlier.

```angular2html
development.driver=com.mysql.jdbc.Driver
development.username=USERNAME -> replace
development.password=PASSWORD -> replace
development.url=jdbc:mysql://localhost/refactoring_analysis
```
* If you wish, you can choose a different name for the database (```refactoring_analysis``` in the template)

* Open the terminal in ```IntelliJ IDE``` run the commands below:

```angular2html
./mvnw clean activejdbc-instrumentation:instrument compile assembly:single clean
java -jar refactoring-analysis.jar
```

(You may have to run the commands ```sudo unlink /etc/localtime``` and ```ln -sf /usr/share/zoneinfo/UTC /etc/localtime``` to change the timezone to the local time. More info about timezone [here](https://unix.stackexchange.com/questions/110522/timezone-setting-in-linux)))

Download the like [repList.txt](../../../files/repoList.txt) and replace it with of the default **reposList.txt** in the cloned project [RefactoringsInMergeCommits](https://github.com/ualberta-smr/RefactoringsInMergeCommits)
<br/>

**Generate stat summaries**
After the program has finished running, you can use the Python scripts in the [stats](https://github.com/ualberta-smr/RefactoringsInMergeCommits/tree/master/stats) folder to look at the results.

* [data_resolver.py](https://github.com/ualberta-smr/RefactoringsInMergeCommits/blob/master/stats/data_resolver.py): This script will print a summary of stats, including total number of merge scenarios, merge scenarios with involved refacotirngs, conflicting regions with involved refactorings, etc.
* [plotter.py](https://github.com/ualberta-smr/RefactoringsInMergeCommits/blob/master/stats/plotter.py): This script can draw a number of different plots.

Task 1.2
===========
Scan through the code and understand how these different refactoring aware operations are implemented:
1. Detecting conflicting regions
2. Detecting evolutionary changes
3. Detecting refactorings (notice that only a few refactoring operations have been implemented this tool. In the [Project](/teaching/Software-Reengineering/project/), you will be required to extend this tool with more refactoring operations)
4. Detecting refactorings in the conflicting region

The above steps are explained in detail in **Section 3: Methodology** of the paper [Are Refactorings to Blame? An Empirical Study of Refactorings in Merge Conflicts](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8668012&tag=1). Of course reading the whole paper would be ideal, but reading only Section 3 should be sufficient.

You could also export the sql structure from the database and reverse engineer the ER diagram using **MySql Workbench** to Understand how the different tables are interconnected 

Task 1.2 - Optional
=================
Looking at the tool [Refactorings in Merge Commits](https://github.com/ualberta-smr/RefactoringsInMergeCommits) we can see that only a subset of the refactoring operations mentioned in the Readme.md of tool [RefactoringMiner](https://github.com/tsantalis/RefactoringMiner/tree/intellij-psi)
have been implemented. Extend [Refactorings in Merge Commits](https://github.com/ualberta-smr/RefactoringsInMergeCommits) with a set of more refactoring operations. Write and run tests to ensure that they have been well implemented.

**Note:** [RefactoringsInMergeCommits](https://github.com/ualberta-smr/RefactoringsInMergeCommits) implements refactoring operations of  [RefactoringMiner](https://github.com/tsantalis/RefactoringMiner/tree/intellij-psi) version 2.1.0. Some on the new refactorings are only present in later versions of the tool.

You may find the following links interesting that will help you in the project:
* [```git log```](https://git-scm.com/docs/git-log). In the [Project](/teaching/Software-Reengineering/project/) we shall be mining data for analysis from the ```git log```. Therefore, it is very important to understand how they are implemented ```git log``` these two projects: [Refactorings in Merge Commits](https://github.com/ualberta-smr/RefactoringsInMergeCommits) and [Refactoring-Aware Merging](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation). **Please read the code in depth**
* [```git cherry-pick```](https://github.com/git/git/blob/90b7153806af46ca62b85a92a2810015be2453d4/Documentation/git-cherry-pick.txt) or in general the [git documentation](https://github.com/git/git/tree/90b7153806af46ca62b85a92a2810015be2453d4/Documentation)

[RefactoringsInMergeCommits](https://github.com/ualberta-smr/RefactoringsInMergeCommits) implements **git merge**, but in the [Project](/teaching/Software-Reengineering/project/) the command **git merge** will be replaced with [**git cherry-pick**](https://github.com/git/git/blob/90b7153806af46ca62b85a92a2810015be2453d4/Documentation/git-cherry-pick.txt)

Task 2 (Optional)
==========
Scan through the code and understand how the following refactoring-aware operations are implemented (First Contact - Readall the Code in One Hour OORP, p.53).
1. Detect and Simplify Refactorings
2. Invert refactorings
3. Merge
4. Detect Refactoring Conflicts
5. Replay Refactorings

The above steps are described in detail in the paper: **Section 3 - REFMERGE: REFACTORING-AWARE OPERATION BASED MERGING** of the paper [A Systematic Comparison of Two Refactoring-aware Merging Techniques](https://arxiv.org/pdf/2112.10370.pdf)

Task 2.1 - Optional
========
[Refactoring-Aware Merging](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation) is a robust project comprising of two tools RefMerge and an Evaluation tool. 
 We are only interested [RefMerge](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation/tree/master/src/main/java/ca/ualberta/cs/smr/refmerge) that performs refactoring-aware merging operations.
[Refactoring-Aware Merging](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation) will be used in the final project, take time to understand how it is implemented. <br/>

## How to run
Follow the instruction on the [Readme.md file](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation) of the project to build and run the project. <br/>

**You may also use the following steps that were adapted from the [Readme.md file of RefMerge](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation) and [Readme.md file of RefactoringMiner](https://github.com/tsantalis/RefactoringMiner/tree/intellij-psi)** <br/>
1. **Clone and build ```RefactoringMiner```** <br/>
Use **git clone https://github.com/tsantalis/RefactoringMiner.git** to clone RefactoringMiner. Then build 
RefactoringMiner with ```./gradlew distzip```. It will be under build/distributions. <br/>
2. In order to use RefactoringMiner as a maven dependency in your project, you will need to **add RefactoringMiner to your local maven repository** <br/>

3. Add the following snippet to your project's build configuration file: <br/>

~~~ xml
<dependency>
  <groupId>com.github.tsantalis</groupId>
  <artifactId>refactoring-miner</artifactId>
  <version>2.1.0</version> 
</dependency>
~~~

 **mvn install:install-file -Dfile=build/libs/RefactoringMiner-2.2.0.jar -DgroupId=com.github.tsantalis -DartifactId=refactoring-miner -Dversion=2.2.0 -Dpackaging=jar -DgeneratePom=false**

3. Build the project
Click on build tab in the IntelliJ IDE and select Build Project to build RefMerge.

Task 2.2 - Optional
=================
Looking at the tool [RefMerge](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation/tree/master/src/main/java/ca/ualberta/cs/smr/refmerge) we can see that only a subset of the refactoring operations mentioned in the Readme.md of tool [RefactoringMiner](https://github.com/tsantalis/RefactoringMiner/tree/intellij-psi)
have been implemented. Extend [RefMerge](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation/tree/master/src/main/java/ca/ualberta/cs/smr/refmerge) with a set of more refactoring operations. Write and run tests to ensure that they have been well implemented.






