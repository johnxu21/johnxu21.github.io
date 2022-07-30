`---
layout: page
title: Refactoring Assistants
permalink: /teaching/CS473-Fall2022/refactoring/
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

In this session, we will learn about some different tools available for refactoring assistance. By using tools, we can plan ahead the refactorings activities that could improve our design. We will search for bad smells (symptoms of design problems) that give us hints on where and how to refactor. When planning refactoring activities, keep in mind the pattern "Keep it Simple" (OORP, p.37), as it a common mistake for people to over-complicate the design of a refactored artifact. Another important pattern to remember when refactorings is “Most Valuable First” (OORP, p.29), as in you should prioritize the refactorings that bring more benefits first.

During this session, we will perform simple refactoring tasks. However, it is important to remember that for the Course we focus on Strategic Refactoring, i.e., we should refactor with a clear reason or goal in mind. 
<br/>


Materials & Tools Used for this Session
========
* Lecture sides [here]()
* [IntelliJ IDE](https://www.jetbrains.com/idea/) (you can use [Eclipse](https://www.eclipse.org/) at your discretion, but it may require some adaptations for the project we are using during the lab sessions)
* [JPacman](https://github.com/johnxu21/jpacman) repository.
* [CodeScene](https://codescene.com/) - **no** installation necessary, but it requires a GitHub account. This tool integration with GitHub allows it to visualize your repositories. The Technical Debt part show refactoring targets. The Code Biomarkers show a more detailed analysis of smells but it is only available to paid subscribers.
* [RefactoringMiner](https://github.com/tsantalis/RefactoringMiner/tree/intellij-psi) is an API/tool that detects the history of refactorings applied to a project.
* [SonarQube](https://www.sonarqube.org/) is a tool/platform that performs static analysis on source codes. Download the free community edition. 

<br/>


Auxiliary Tools
============
Auxiliary tools are not required for the lab session itself, but they may be useful to get additional information (or alternatives) on a project. Use them at your own discretion. 
* [PMD](https://pmd.github.io/) is a tool for analyzing source code, it can detect some smells and bad practices.
* [JDeodorant](https://github.com/tsantalis/JDeodorant) is an Eclipse plugin that detects some Code Smells and recommends appropriate refactorings to "fix" them. It supports these design smells: Type Checks, Feature Envy, God Class, Long Parameter. JDeodorant is famous in academia, so much that everyone doing work on refactoring/smells compares it with JDeodorant.
* [JMove](https://github.com/aserg-ufmg/jmove) is another Eclipse plugin, specialized in performing only move method refactorings. Therefore, it is a good tool to detect the [Feature Envy smell](https://www.haselt.com/blog/refactoring-a-feature-envy-code).

<br/>

Setup / Preparation
=============
Be sure to follow the setup from the first session ([Metrics and Visualization Lab Session](/teaching/CS473-Fall2022/metrics/)) if you had not done so (summarizing it would be: 
(i) install IntelliJ, (ii) fork JPacman repository, (iii) build & run JPacman). 
Also if have not already, download the book for this course "[Object-Oriented Reengineering Patterns](http://scg.unibe.ch/download/oorp/)" (Note: OORP, p.xx refers to a page in the pdf version of this book)

Get/Install the tools & plugins detailed in the Materials above (not the auxiliary tools, they are optional and will not be used in this lab session).
<br/>


Task 1 -- JPacman on CodeScene
=========
 
For our first task, we are going to use CodeScene to suggest which artifacts are in need of refactoring. If you did the setup from the Metrics and Visualization lesson, you should already have JPacman in your CodeScene. If not, go to the CodeScene, login (or create a new free account), and add JPacman so you can see it on the CodeScene interface.
 
Click in the "Code" menu on the left side, and then the "Hotspots" submenu. In this visualization, the hotspots are artifacts with a lot of commit activities (i.e., they change a lot during the software evolution and maintenance). On that visualization, you can check the tab on Refactoring Targets. Look at the recommended refactorings targets. If you select a specific file in this visualization (or the hotspots visualization) on the right it will display more details, scrolling down on the details you have the "Actions" buttons. There are four actions: View Code, X-ray, Trends, and Code Review. Check those four options and see for yourself what information CodeScene can provide.

Questions:
* Did CodeScene visualization help you identify possible targets for refactoring?
* Did CodeScene give you hints or clues on how to refactor the proposed targets?
<br/>




Task 2 -- JPacman on SonarQube
============
For the second task, we are going to use a more complex and dedicated tool to find refactoring targets. Download SonarQube (if you haven't already), and unpacked it on your computer. We will need to use command lines to start the SonarQube tool (note that you need to have Java JDK 11 to run the current version of SonarQube).  Open a Terminal (Command Prompt on Windows) and make sure you are currently on the SonarQube folder. Then, you should go into the bin folder like for example:

**cd bin**

Inside the bin folder of SonarQube, you will find specific folders for each major operating system. Go into the appropriate folder for your machine operating system. For example, on a machine running Mac OsX the command will be:

**cd macosx-universal-64**

Now you can start the SonarQube using the command:

**[ Linux / Mac ] ./sonar.sh console** <br>
**[ Windows ] StartSonar.bat**

If you are having problems, please check the [SonarQube Documentation](https://docs.sonarqube.org/latest/) (here is the Getting [Started guide](https://docs.sonarqube.org/latest/setup/get-started-2-minutes/)). If everything went ok, then you should see in your terminal a message like "<date> INFO yyy [ xxxx ] SonarQube is up" (it may take some time). Now open your browser and type the following address on it:

**http://localhost:9000**

Click on "Log In" (top-right corner). The login is "admin" and the password is also "admin". After the login, you will be required to change the password for the admin account. In the lab assignments, my password is "reengineering" (adapt to your chosen password accordingly).

Now you will see the page for "Analyze your Project". In the first step, for the token name type "jpacmantoken". Click on "generate" and then "continue" (remember or save this generated code for step 2).

If everything was ok, then you should see step 2. Select "Gradle" on the build technology options. You can follow the instructions given but for this lab session, you can just keep following here. So the first thing to do is update your build Gradle file (if you fetched the last version of the repository, this is not necessary). Open your IntelliJ with the JPacman sources, and in the project root folder you will find the "build.gradle" file. Open the file and add this line after line 7 (inside the "plugins" element):

**id "org.sonarqube" version "3.1.1"**

Now you can use the terminal inside IntelliJ for the command given by SonarQube, place all in the same line (adapt the command accordingly for Windows):

**./gradlew sonarqube -Dsonar.projectKey=jpacman  
   -Dsonar.host.url=http://localhost:9000 -Dsonar.login=<generated token code>**

If you are having problems with the above command, try this one instead:

**./gradlew sonarqube -Dsonar.projectKey=JPacman  
    -Dsonar.host.url=http://localhost:9000 -Dsonar.login=admin -Dsonar.password=reengineering**

If everything was ok, then the page on SonarQube should update in a while with JPacman source code information. Here is a screenshot of SonarQube once it finishes its analysis on JPacman.
 
Click on the "Code Smells" and analyze the detected smells. You can also see that SonarQube also gives some explanation of the smells ("Why is this an issue?"). 

Questions:
* Which one is more useful to find refactoring targets: CodeScene or SonarQube?
* Which one provides better reasoning/explanation on the possible refactoring targets: CodeScene or SonarQube?
* Are there many common artifacts found in the Code Smells in SonarQube and Refactoring targets in CodeScene?
<br/>


Task 3 -- JPacman Strategic Refactoring
===============
For the Reengineering Course, we value the concept of Strategic Refactoring, which is refactoring with a goal. Tools can help identify artifacts with smells that could lead to potential issues. However, only a developer can really identify the necessary artifacts for a specific goal. Let's do that for JPacman. 
 
As you probably noticed, JPacman is missing many features that were present in the original Pacman game. Now, the idea is to start refactoring the code to support one of those missing features: Extra Lives. In the original Pacman, the player started with 3 lives. In JPacman, there is only 1 life, and if lose it: game over. If you look at the code (Player.java) there is no attribute to store how many lives the player has left. 
 
Look at JPacman's artifacts and plan the necessary refactoring(s) to support multiple lives. You can start on the simplest refactorings as to not "break" the code or go big according to the pattern "Most Valuable First". There is no wrong path here, do whichever you think is easier or most logical for you. Please note, you need only to "plan" the refactorings for this lab session there is no need to actually apply the refactorings on the code (of course, if you want to do it, go ahead --- just remember that planning is the important part here).
 
Questions:
* Which were your strategies and reengineering patterns for planning this refactoring? 
* Why did you consider these refactorings important for your goal?
* Did the previous tools (CodeScene or SonarQube) identify the refactoring targets you deemed necessary for this goal?
* Do you prefer to refactor just to improve code quality or to refactor with a goal?
<br/>


Optional Task  1 -- JPacman Strategic Refactoring (part 2)
===========

For this optional task, you should apply the planned refactorings from the last task on the source code. Remember to assure that your refactorings are not breaking the application.

