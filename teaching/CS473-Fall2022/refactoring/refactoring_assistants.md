---
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
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
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

In this session, we will learn about some different tools available for refactoring assistance. 
By using tools, we can plan ahead the refactorings activities that could improve our design. 
We will search for bad smells (symptoms of design problems) that give us hints on where and how 
to refactor. When planning refactoring activities, keep in mind the pattern "Keep it Simple" 
(OORP, p.37), as it a common mistake for people to over-complicate the design of a refactored 
artifact. Another important pattern to remember when refactorings is “Most Valuable First” 
(OORP, p.29), as in you should prioritize the refactorings that bring more benefits first.

Despite the benefits, in some contexts, refactoring is perceived as change noise, which makes more 
difficult the completion of various software evolution related tasks. For instance, refactoring 
operations can cause merge conflicts when merging development branches (we shall look this in detail in 
Lab of [software integration](/teaching/CS473-Fall2022/integration/)). 
They may distract developers when reviewing behavior-altering changes, make bug-inducing analysis algorithms
to erroneously flag behavior-preserving changes (i.e., refactorings) as bug-introducing, 
cause breaking changes to clients of libraries and frameworks, cause unnecessary test executions 
for behavior-preserving changes.

During this session, we will perform simple refactoring tasks. However, it is important to remember 
that for the Course we focus on Strategic Refactoring, i.e., we should refactor with a clear 
reason or goal in mind. 
<br/>


Materials & Tools Used for this Session
========
* Lecture sides [here](../../../files/Refactoring_Assistants.pdf)
* [IntelliJ IDE](https://www.jetbrains.com/idea/) (you can use [Eclipse](https://www.eclipse.org/) at your discretion, but it may require some adaptations for the project we are using during the lab sessions)
* [JPacman](https://github.com/johnxu21/jpacman) repository.
* [CodeScene](https://codescene.com/) - **no** installation necessary, but it requires a GitHub account. This tool integration with GitHub allows it to visualize your repositories. The Technical Debt part show refactoring targets. The Code Biomarkers show a more detailed analysis of smells but it is only available to paid subscribers.
* [SonarQube](https://www.sonarqube.org/) is a tool/platform that performs static analysis on source codes. Download the free community edition. 
* [RefactoringMiner](https://github.com/tsantalis/RefactoringMiner/tree/intellij-psi) is a Refactoring-aware API/tool that detects the history of refactorings applied to a project.

<br/>


Auxiliary Tools
============
Auxiliary tools are not required for the lab session itself, but they may be useful to get additional information (or alternatives) on a project. Use them at your own discretion. 
* [PMD](https://pmd.github.io/) is a tool for analyzing source code, it can detect some smells and bad practices.
* [JDeodorant](https://github.com/tsantalis/JDeodorant) is an Eclipse plugin that detects some Code Smells and recommends appropriate refactorings to "fix" them. It supports these design smells: Type Checks, Feature Envy, God Class, Long Parameter. JDeodorant is famous in academia, so much that everyone doing work on refactoring/smells compares it with JDeodorant.
* [JMove](https://github.com/aserg-ufmg/jmove) is another Eclipse plugin, specialized in performing only move method refactorings. Therefore, it is a good tool to detect the [Feature Envy smell](https://www.haselt.com/blog/refactoring-a-feature-envy-code).

<br/>

Setup / Preparation - (Artifacts that need refactoring)
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

**Questions:**
* Did CodeScene visualization help you identify possible targets for refactoring?
* Did CodeScene give you hints or clues on how to refactor the proposed targets?
<br/>




Task 2 -- JPacman on SonarQube
============
For the second task, we are going to use a more complex and dedicated tool to find refactoring targets. Download SonarQube (if you haven't already), and unpacked it on your computer. We will need to use command lines to start the SonarQube tool (note that you need to have Java JDK 11 to run the current version of SonarQube).  Open a Terminal (Command Prompt on Windows) and make sure you are currently on the SonarQube folder. Then, you should go into the bin folder like for example:

```
cd bin
```

Inside the bin folder of SonarQube, you will find specific folders for each major operating system. Go into the appropriate folder for your machine operating system. For example, on a machine running Mac OsX the command will be:

```
cd macosx-universal-64
```

Now you can start the SonarQube using the command:

**[Linux/Mac]** ```./sonar.sh console``` <br>
**[Windows]** ```StartSonar.bat```

If you are having problems, please check the [SonarQube Documentation](https://docs.sonarqube.org/latest/) (
here is the Getting [Started guide](https://docs.sonarqube.org/latest/setup/get-started-2-minutes/)). 
If everything went ok, then you should see in your terminal a message like ```<date> INFO yyy [ xxxx ] SonarQube is up``` 
(it may take some time). Now open your browser and type the following address on it:

```
http://localhost:9000
```

Click on "Log In" (top-right corner). The login is "admin" and the password is also "admin". 
After the login, you will be required to change the password for the admin account. In the lab assignments, 
my password is ```reengineering``` (adapt to your chosen password accordingly).

Now you will see the page for "Analyze your Project". In the first step, for the token name type 
```jpacmantoken```. Click on ```generate``` and then ```continue``` (remember or save this generated code for step 2).

If everything was ok, then you should see step 2. Select ```Gradle``` on the build technology options. 
You can follow the instructions given but for this lab session, you can just keep following here. 
So the first thing to do is update your build Gradle file (if you fetched the last version of the repository, 
this is not necessary). Open your IntelliJ with the JPacman sources, and in the project root folder you will 
find the ``build.gradle`` file. Open the file and add this line after line 7 (inside the ``plugins`` element):

```
id 'org.sonarqube' version '3.1.1'
```

Now you can use the terminal inside ```IntelliJ``` for the command given by ```SonarQube```, place all in the 
same line (adapt the command accordingly for Windows):

```
./gradlew sonarqube -Dsonar.projectKey=jpacman -Dsonar.host.url=http://localhost:9000 -Dsonar.login=[generated token code]
```

If you are having problems with the above command, try this one instead:

```
./gradlew sonarqube -Dsonar.projectKey=JPacman -Dsonar.host.url=http://localhost:9000 -Dsonar.login=admin -Dsonar.password=reengineering
```

If everything was ok, then the page on SonarQube should update in a while with ```JPacman``` source code information. 
Here is a screenshot of SonarQube once it finishes its analysis on ```JPacman```.
 
Click on the ```Code Smells``` and analyze the detected smells. You can also see that SonarQube also gives some 
explanation of the smells ("Why is this an issue?"). 

**Questions:**
* Which one is more useful to find refactoring targets: ```CodeScene``` or ```SonarQube```?
* Which one provides better reasoning/explanation on the possible refactoring targets: ```CodeScene``` or ```SonarQube```?
* Are there many common artifacts found in the Code Smells in ```SonarQube``` and Refactoring targets in ```CodeScene```?
<br/>


Task 3 -- JPacman Strategic Refactoring
===============
For the Reengineering Course, we value the concept of **Strategic Refactoring**, which is refactoring with a goal. 
Tools can help identify artifacts with smells that could lead to potential issues. However, only a developer can 
really identify the necessary artifacts for a specific goal. Let's do that for JPacman. 
 
As you probably noticed, ```JPacman``` is missing many features that were present in the original Pacman game. 
Now, the idea is to start refactoring the code to support one of those missing features: Extra Lives. 
In the original Pacman, the player started with 3 lives. In JPacman, there is only 1 life, and if lose it: game over. 
If you look at the code (Player.java) there is no attribute to store how many lives the player has left. 
 
Look at JPacman's artifacts and plan the necessary refactoring(s) to support multiple lives. You can start on the 
simplest refactorings as to not "break" the code or go big according to the pattern "Most Valuable First". 
There is no wrong path here, do whichever you think is easier or most logical for you. Please note, you need only to 
"plan" the refactorings for this lab session there is no need to actually apply the refactorings on the code 
(of course, if you want to do it, go ahead --- just remember that planning is the important part here).
 
Questions:
* Which were your strategies and reengineering patterns for planning this refactoring? 
* Why did you consider these refactorings important for your goal?
* Did the previous tools (```CodeScene``` or ```SonarQube```) identify the refactoring targets you deemed necessary for this goal?
* Do you prefer to refactor just to improve code quality or to refactor with a goal?
<br/>


Optional Task  1 -- JPacman Strategic Refactoring (part 2)
===========

For this optional task, you should apply the planned refactorings from the last task on the source code. 
Remember to assure that your refactorings are not breaking the application.


Task 4 - Setup / Preparation - (Refactoring aware)
=============
[RefactoringMiner](https://github.com/tsantalis/RefactoringMiner/tree/intellij-psi) is a library/API written in 
Java that can detect refactoring operations applied in the history of a Java project.

Currently, it supports the detection of the more than 80 refactorings.


Clone&own [RefactoringMiner](https://github.com/tsantalis/RefactoringMiner/tree/intellij-psi) or install from the 
sources directly into Intellij.

You can follow the instructions on the [Readme.md](https://github.com/tsantalis/RefactoringMiner/blob/intellij-psi/README.md) 
of the project (First contact: Skim the Documentation OORP p. 61).

Create a file named ```Main.java``` or any name of your choice under the subdirectory 
```scr/org/refactoringminer/Main.java``` and copy&paste the following code snippet into the file.  
Run the ```Main.java``` file.

```java
public class Main {
    public static void main(String[] args) throws Exception {
        GitService gitService = new GitServiceImpl();
        GitHistoryRefactoringMiner miner = new GitHistoryRefactoringMinerImpl();

        final List<CodeRange>[] sourceCodeRanges = new List[]{new ArrayList<CodeRange>()};
        final List<CodeRange>[] destCodeRanges = new List[]{new ArrayList<CodeRange>()};

        
        // change the temporary folder in case you are examining a different repository
        Repository repo = gitService.cloneIfNotExists(
                "tmp/refactoring-toy-example",
                "https://github.com/danilofes/refactoring-toy-example.git");

        // start commit: 819b202bfb09d4142dece04d4039f1708735019b
        // end commit: d4bce13a443cf12da40a77c16c1e591f4f985b47
        miner.detectBetweenCommits(repo,
                "819b202bfb09d4142dece04d4039f1708735019b", "d4bce13a443cf12da40a77c16c1e591f4f985b47",
            new RefactoringHandler() {
                @Override
                public void handle(String commitId, List<Refactoring> refactorings) {
                    System.out.println("Refactorings at " + commitId);
                    for (Refactoring ref : refactorings) {
                        System.out.println(ref.toString());
                        System.out.println(ref.getName());
                        sourceCodeRanges[0] = ref.leftSide();
                        destCodeRanges[0] = ref.rightSide();
//                        System.out.println(sourceCodeRanges[0].toString());
//                        System.out.println(destCodeRanges[0].toString());
                        System.out.println();

                        System.out.println("SourceCodeRanges");
                        for(CodeRange srcCodeRange: sourceCodeRanges[0]){
                            System.out.println("FilePath: " + srcCodeRange.getFilePath());
                            System.out.println("StartLine : " + srcCodeRange.getStartLine());
                            System.out.println("EndLine : " + srcCodeRange.getEndLine());
                            System.out.println("StartColumn : " + srcCodeRange.getStartColumn());
                            System.out.println("EndColumn : " + srcCodeRange.getEndColumn());
                            System.out.println("codeElementType : " + srcCodeRange.getCodeElementType());
                            System.out.println("Description : " + srcCodeRange.getDescription());
                            System.out.println("codeElement : " + srcCodeRange.getCodeElement());

                        }

                        System.out.println();
                        System.out.println("DestinationCodeRanges");
                        for(CodeRange destCodeRange: destCodeRanges[0]){
                            System.out.println("FilePath: " + destCodeRange.getFilePath());
                            System.out.println("StartLine : " + destCodeRange.getStartLine());
                            System.out.println("EndLine : " + destCodeRange.getEndLine());
                            System.out.println("StartColumn : " + destCodeRange.getStartColumn());
                            System.out.println("EndColumn : " + destCodeRange.getEndColumn());
                            System.out.println("codeElementType : " + destCodeRange.getCodeElementType());
                            System.out.println("Description : " + destCodeRange.getDescription());
                            System.out.println("codeElement : " + destCodeRange.getCodeElement());

                        }

                    }
                }
        });
    }
}
```


In the above task we want to look at the code ranges of the refactoring operations. In the project we shall mainly analyze refactoring operations in commits of a pull request. 
You can try to identify the refactorings operations applied in the project [kafka](https://github.com/apache/kafka) at pull request numbers 8905
8716, 8720, 8571, 8417. <br/>

```java
GitHistoryRefactoringMiner miner = new GitHistoryRefactoringMinerImpl();
miner.detectAtPullRequest("https://github.com/apache/drill.git", 1807, new RefactoringHandler() {
  @Override
  public void handle(String commitId, List<Refactoring> refactorings) {
    System.out.println("Refactorings at " + commitId);
    for (Refactoring ref : refactorings) {
      System.out.println(ref.toString());
    }
  }
}, 10);
```

**QN: What are the most common refactorings operations present in these pull requests?**

Try out the different API usage guidelines mentioned on the [Readme.md](https://github.com/tsantalis/RefactoringMiner/blob/intellij-psi/README.md) page.

Task 5
==========
Scan through the code and understand how the different refactorings are detected (First Contact - Readall the Code in One Hour OORP, p.53).
Note down the entities which seem important (i.e., classes, packages, ···). This step will help you during the [Project](/teaching/CS473-Fall2022/project/).

"**Intent:** Assess the state of a software system by means of a brief, but intensive code review."

Additional Reading Material
=============

In case you want to dive deeper into refactoring, here are some extra materials about it.

1. M. Fowler, K. Beck, J. Brant, W. Opdyke, and D. Roberts. Refactoring: Improving the Design of Existing Code. Object Technology Series. Addison-Wesley, 1 edition, June 1999.
2. M. Lanza and R. Marinescu. Object-Oriented Metrics in Practice - Using Software Metrics to Characterize, Evaluate, and Improve the Design of Object-Oriented Systems. Springer, 2006.
3. M. Fowler and J. Kerievsky. Smells to refactorings quick reference guide. reference sheet, 2005.: http://www.industriallogic.com/blog/smells-to-refactorings-cheatsheet/
4. F. Khomh, M. D. Penta, Y.-G. Guéhéneuc, and G. Antoniol. An exploratory study of the impact of antipatterns on class change- and fault-proneness. Empirical Softw. Engg., 17(3):243–275, June 2012. http://link.springer.com/article/10.1007%2Fs10664-011-9171-y
5. Nikolaos Tsantalis, IEEE, Ameya Ketkar, and Danny Dig, [Refactoring 2.0](https://users.encs.concordia.ca/~nikolaos/publications/TSE_2020.pdf). 2020

