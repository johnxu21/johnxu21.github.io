---
layout: page
title: Refactoring Assistants
permalink: /teaching/Software-Reengineering/refactoring/
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
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Refactoring Assistants" />
</form>
<form action="/teaching/Software-Reengineering/dynamic/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Dynamic Analysis: Testing" />
</form>
<form action="/teaching/Software-Reengineering/integration/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
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

In this session, we will look at some of the tools available for refactoring assistance. Tools let us plan
ahead the refactoring activities that could improve our design: we search for bad smells (symptoms of design
problems) that give us hints on where and how to refactor. When planning refactoring activities, keep in mind
the pattern "**Keep It Simple**" (OORP, p.37), as it is a common mistake to over-complicate the design of a
refactored artifact. Another important pattern to remember when refactoring is "**Most Valuable First**"
(OORP, p.29): prioritize the refactorings that bring the most benefit first.

Despite these benefits, refactoring is in some contexts perceived as change noise, which makes various software
evolution tasks harder to complete. Refactoring operations can cause merge conflicts when merging development
branches (we will look at this in detail in the
[Software Integration](/teaching/Software-Reengineering/integration/) lab). They may also distract developers who
are reviewing behavior-altering changes, cause bug-inducing analysis algorithms to erroneously flag
behavior-preserving changes (i.e., refactorings) as bug-introducing, break clients of libraries and frameworks,
and trigger unnecessary test executions for behavior-preserving changes.

During this session, we will perform simple refactoring tasks. However, it is important to remember that in this
course we focus on Strategic Refactoring, i.e., we refactor with a clear reason or goal in mind.

**In this session you will:**

* use CodeScene to identify and prioritize refactoring targets in a large system;
* use SonarQube to find and interpret code smells in that same system;
* plan refactorings that serve a concrete goal (Strategic Refactoring) rather than code quality alone;
* argue when a tool-proposed refactoring target is worth acting on -- and when it is not.

Materials & Tools Used for this Session
========

**Slides**

* [Refactoring Assistants (PDF)](../../../files/Refactoring_Assistants.pdf)

**Project**

* [django CMS](https://github.com/django-cms/django-cms) -- the same large Python system you analyzed in the
  [Metrics and Visualization](/teaching/Software-Reengineering/metrics/) session.

**IDE**

* [PyCharm](https://www.jetbrains.com/pycharm/) -- the Community Edition is sufficient; any other IDE works as well.

**Tools**

* [CodeScene](https://codescene.com/) -- **no** installation necessary, but it requires a GitHub account. Its
  GitHub integration lets it visualize the repositories in your account. The **Technical Debt** section shows
  refactoring targets. The **Code Biomarkers** give a more detailed analysis of smells, but they are only
  available to paid subscribers.
* [SonarQube](https://www.sonarqube.org/) -- a platform that performs static analysis on source code. Download the
  free Community Edition.

**Book**

* [Object-Oriented Reengineering Patterns](http://scg.unibe.ch/download/oorp/) (OORP)
  (_Note: OORP, p.xx refers to a page in the pdf version of this book_)

<br/>

Setup / Preparation
=============

1. **Complete the setup from the first session**
   ([Metrics and Visualization](/teaching/Software-Reengineering/metrics/)). In particular, you need your fork of
   django CMS analyzed in CodeScene and cloned locally.
2. **Download the book**, if you have not already:
   "[Object-Oriented Reengineering Patterns](http://scg.unibe.ch/download/oorp/)".

> **Note:** You are only required to **plan** the refactorings for this lab. Implementing them is optional
> (see Optional Task 1).

> **Tip:** take screenshots while you work. You will need evidence of tool usage for the
> [Intermediate Report](/teaching/Software-Reengineering/project/) later in the semester.

<br/>

Task 1: django CMS on CodeScene
=========
For our first task, we are going to use CodeScene to suggest which artifacts are in need of refactoring.

Open the CodeScene analysis of your django CMS fork, select the "**Code**" menu on the left side, and then the
"**Hotspots**" submenu. In this visualization, the hotspots are artifacts with a lot of commit activity (i.e.,
they change a lot during software evolution and maintenance). From there, open the **Refactoring Targets** tab
and look at the recommended targets.

If you select a specific file in either visualization, the panel on the right displays more details. Scroll down
to the details section and you will find a few actions: **Review**, **Source code**, and **X-Ray**. Try them out
and see for yourself what information CodeScene can provide.

Also notice that, for some files, CodeScene highlights other coupled files. Explore these code couplings as well.

**Questions:**

* Did the CodeScene visualization help you identify possible targets for refactoring?
* Did CodeScene give you hints or clues on *how* to refactor the proposed targets?
* Did CodeScene help you gauge the extent of the refactoring activity?

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **Most Valuable First** *(p.29)* -- Prioritize the refactoring opportunities that offer the highest benefit or
  reduce the most risk, rather than the ones that are easiest to spot.
- **Keep It Simple** *(p.37)* -- Avoid the temptation to over-engineer when identifying or planning a refactoring.
- **Study the Exceptional Entities** *(p.107)* -- CodeScene reveals the outliers in complexity and change
  frequency that often signal deeper design problems.

<br/>

Task 2: django CMS on SonarQube
============
For the second task, we will use a more complex and dedicated tool to find refactoring targets. Follow the
instructions in the [documentation](https://docs.sonarsource.com/sonarqube-server/latest/try-out-sonarqube/) to
install and run SonarQube. You may either install it locally or run it in a Docker container.

> **Important:** for Mac M-series users,
> [Docker](https://docs.docker.com/desktop/setup/install/mac-install/) is the recommended and generally easiest
> installation option, rather than the "From the zip file" option. If you run into any issue, please reach out to
> the TAs for help.

If you are successful, you should be able to run an analysis of your local clone of django CMS.

Click on "**Code Smells**" and analyze the detected smells. You will see that SonarQube also explains each smell
("Why is this an issue?").

**Questions:**

* Did SonarQube help you identify specific design problems (code smells) that CodeScene did not?
* Which smells stood out to you as most critical to address, and why?
* Were there any cases where the smell detection was misleading or not worth acting on?

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **Split Up God Class** *(p.263)* -- Apply this when you encounter very large classes that take on too many
  responsibilities. Such classes become maintenance bottlenecks and are error-prone; SonarQube tends to surface
  them through complexity, duplication, or high coupling.
- **Refactor to Understand** *(p.127)* -- If the code is hard to follow, small and safe refactorings such as
  Rename Method or Extract Method improve clarity and help you reason about the structure before attempting more
  extensive changes.
- **Step Through the Execution** *(p.133)* -- When unsure about the implications of a smell, walk through how the
  code behaves at runtime to validate whether a static smell points to a real design issue.

<br/>

Task 3: django CMS Strategic Refactoring
========
In this course, we value the concept of Strategic Refactoring: refactoring with a goal. Tools can point out
artifacts with smells that could lead to potential issues. However, only a developer can decide which artifacts
matter for a specific goal. Let's do that for django CMS.

Browse the [issue tracker](https://github.com/django-cms/django-cms/issues) of django CMS and search for issues
with the query `is:open label:"kind: enhancement"`. You will notice that some of these issues require a patch.

Choose a few issues and plan the refactoring task(s) needed to support them. You can start with the simplest
refactorings to avoid "breaking" the code, or go big according to "**Most Valuable First**". There is no wrong
path -- do whichever you find easier or more logical.

**Questions:**

* What were your strategies and reengineering patterns for planning this refactoring?
* Why did you consider these refactoring tasks important for your goal?
* Did the previous tools (CodeScene or SonarQube) identify the refactoring targets you deemed necessary for this
  goal?
* Do you prefer to refactor to improve code quality, or to refactor with a goal?

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **Refactor to Understand** *(p.127)* -- If the area of the code you are planning to change is hard to
  understand, use safe refactorings (renaming, extracting methods) to gain clarity before deeper changes.
- **Learn from the Past** *(p.141)* -- Compare earlier versions of the code and look at how similar functionality
  was added, moved, or removed. The history tells you which parts of the design already absorb change well and
  which parts fight it.
- **Most Valuable First** *(p.29)* -- Rank the candidate refactorings by the value they deliver for the
  enhancement you picked.

<br/>

Optional Task 1: django CMS Strategic Refactoring (Part 2)
===========
To complete this optional task, implement the refactoring tasks you planned in Task 3. Remember to ensure that
your refactoring does not break the application.

Optional Task 2: Duplicate Code Detection on SonarQube
==========
If you looked over the SonarQube analysis of django CMS, you may have noticed that the tool also detects
duplicated code. Check out how SonarQube presents the duplicates it found. This is a first look at
"**Detecting Duplicated Code**" (OORP, p.223), a topic we return to later in the course.

* Did you like SonarQube's visualization of duplicated code snippets?
* Would you prefer another tool? Why do you like your chosen tool?

Additional Reading Material
=============

In case you want to dive deeper into refactoring, here are some extra materials.

1. M. Fowler, K. Beck, J. Brant, W. Opdyke, and D. Roberts. *Refactoring: Improving the Design of Existing Code*.
   Object Technology Series. Addison-Wesley, 1st edition, June 1999.
2. M. Lanza and R. Marinescu. *Object-Oriented Metrics in Practice -- Using Software Metrics to Characterize,
   Evaluate, and Improve the Design of Object-Oriented Systems*. Springer, 2006.
3. M. Fowler and J. Kerievsky.
   [Smells to Refactorings Quick Reference Guide](http://www.industriallogic.com/blog/smells-to-refactorings-cheatsheet/).
   Reference sheet, 2005.
4. F. Khomh, M. Di Penta, Y.-G. Guéhéneuc, and G. Antoniol.
   [An exploratory study of the impact of antipatterns on class change- and fault-proneness](http://link.springer.com/article/10.1007%2Fs10664-011-9171-y).
   Empirical Software Engineering, 17(3):243-275, June 2012.
5. N. Tsantalis, A. Ketkar, and D. Dig.
   [RefactoringMiner 2.0](https://users.encs.concordia.ca/~nikolaos/publications/TSE_2020.pdf).
   IEEE Transactions on Software Engineering, 2020.

Post-Lab Quiz: Refactoring Assistants
==========
The quiz for this session is posted on WebCampus.
