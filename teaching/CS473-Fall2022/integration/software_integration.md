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
* Lecture sides [here]()
* [IntelliJ IDE](https://www.jetbrains.com/idea/) (you can use [Eclipse](https://www.eclipse.org/) at your discretion, but it may require some adaptations for the project we are using during the lab sessions)
* [RefactoringsInMergeCommits](https://github.com/ualberta-smr/RefactoringsInMergeCommits) 
* [Refactoring-Aware Merging](https://github.com/ualberta-smr/RefactoringAwareMergingEvaluation)

