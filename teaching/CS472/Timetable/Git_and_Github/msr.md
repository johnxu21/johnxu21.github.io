---
layout: page
title: CS472 - Git and GitHub
permalink: /teaching/CS472/Timetable/Git_and_GitHub/
---

<div class="main-component">
<form action="/teaching/CS472/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>

<form action="/teaching/CS472/Timetable/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Timetable" />
</form>
<form action="/teaching/CS472/Exam/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Exam" />
</form>
<form action="/teaching/CS472/project/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Project" />
</form>
</div>
<br/>

Labs
=======
<div class="main-component">
<form action="/teaching/CS472/Timetable/Git_and_GitHub/">
    <input type="submit" style="background-color:firebrick;float:left; color:white;width:130px;
height:30px;" value="Git & GitHub" />
</form>
<form action="/teaching/CS472/Timetable/dynamic_analysis/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="Testing" />
</form>
<form action="/teaching/CS472/Timetable/CI/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="CI" />
</form>
<form action="/teaching/CS472/Timetable/GPT/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="CHAT GPT" />
</form>
</div>

<br/>
<br/>


### **This individual assignment is due September 13th, 2023**

For this lab, you will be learning how to explore an open 
source repository from GitHub. You will also learn how to extract useful 
information from the repository and practice your project management skills by 
writing a short executive summary on your findings. 
(This assignment assumes you have installed git on your computer.  
If you haven't done this yet look at the Pro Git book or online for help.)

### Part 1. Clone your team's repository and add files (5 pts)

By now, everyone should have a GitHub account and been given added to the 
team's repository as ```collaborators```. In the team repository there should be a file ```contributors.txt```
that contains the contributor list of the team.

**Invite me and the TA as collaborators on your repository.**  
* my [GitHub ID - ```johnxu21```](https://github.com/johnxu21)).
* TA [GitHub ID: ```Godlander```](https://github.com/Godlander)

Fork the teams repository and clone the fork onto your laptop.
* create a branch on your local repository called ```contributors``` using the following command ```git branch contributors```.
* run the command ```git checkout contributors```
* edit the ```contributors.txt``` and add your ```name``` and ```email address```.
* type the following commands
```commandline
git add contributors.txt
git commit -m "your commit message here"
git push
```
<img src="/teaching/CS472/Timetable/Git_and_Github/contributors.jpeg" alt="contributors" style="width:600px;height:376px;" align="center">
 
* in your fork on GitHub, you should be able to see a screen like the image above.
* open a pull request and write an appropriate title and body.
* one of the repository maintainers should integrate your contribution.


### Part 2. Add a new file to the repository (20 pts)

* create a folder on your local fork repository called ```repo_mining```
* create and checkout a new branch on your local fork repository using the following command ```git checkout -b mine_repository```
* clone my repo [johnxu21/msrLab](https://github.com/johnxu21/msrLab) in a separate local repository
* browse the ```src``` folder and copy the file ```CollectFiles.py``` into the ```repo_mining``` folder on your forks' local repository
* Rename the file ```CollectFiles.py``` to ```<your-names>_CollectFiles.py```.
* generate a [GitHub token](https://github.com/settings/tokens/new?scopes=repo) that you will use to mine content using the GitHub API
* Replace the fake ```tokens``` in the code of ```<your-names>_CollectFiles.py``` with the token you have just generated.
* Thereafter, run the file ```<your-names>_CollectFiles.py``` and look at the output. 
The code collects all the files in a repo and also the number of counts the file is touched 
throughout its lifetime.

**Caution:** When pushing your changes to GitHub, **replace your token with fake digits or delete it completely**. 
If you push your code without removing the token, it will be reverted, and you will have to regenerate it again.

A repository contains both source files and other files like configuration files. Developers 
spend most of the time changing source files for many reasons, for example, fixing bugs, 
extending them with new features, or refactoring. The script CollectFiles.py collects all 
files in a repository. So your first task is to adapt the script to gather only the source files. 
You can find a repo's programming languages on the bottom right of the repo's page on GitHub 
(some repos could be written in more than one programming language).
* First, write a script with the name ```<'your_firstname'_authorsFileTouches.py>``` that collects 
the authors and the dates when they touched for each file in the list of files generated by the 
adapted file CollectFiles.py (only source files).
* Second, write a script that generates a scatter plot (using matplotlib) of weeks vs file 
variables where the points are shaded according to author variable. Each author should have 
a distinct color. Looking at the scatter plot one should be able to tell a file that is 
touched many times and by whom. This can help, for example, when identifying refactoring 
opportunities, which developer should be allocated the task since they have touched a file 
many times or have recently worked on the file. You can name the script for drawing the 
histogram ```<'your_firstname'_scatterplot.py>```. 
You get a hint on how draw the scatter plot on this link on [Stackoverflow](https://stackoverflow.com/questions/8202605/matplotlib-scatterplot-color-as-a-function-of-a-third-variable).


**Example** ([scottyab/rootbeer](https://github.com/scottyab/rootbeer)) <br/>
The repository scottyab/rootbeer has a total of 17+ unique source files. It has a total 
of 33+ authors who have touched the 17+ unique files (the data points in the graph) who have been 
updating the files and committing their changes. The scatter plot  below  shows the authors 
activities over time for the repository scottyab/rootbeer. 

<img src="/teaching/CS472/Timetable/Git_and_Github/rootbeer.jpeg" alt="rootbeer" style="width:600px;height:480px;" align="center">

### Part 3. Executive Summary (5 pts)

Pretend you are a project manager writing a status report on the [scottyab/rootbeer](https://github.com/scottyab/rootbeer) project 
to your boss as if it was a company-owned project.  The report should take the 
form of an Executive Summary. Your boss is very busy and overworked, and he won't 
bother reading more than a page, so write clearly and succinctly. Charts and 
graphs also grab his attention compared to walls of text, and he's getting older 
and can't read 9 point font, so don't try to pack too much in.  Focus on the 
main highlights and high level communication. This is an important project for 
the company, so the report will likely go up the ladder (maybe even to the Board)
, so make sure it's formatted nicely and without grammar errors or typos.  
You can include things from the reporting you did in Part 2 (or do more 
yourself) and it should focus on things like how much work is being done, who 
is doing it? who is doing the most work overall and in recent weeks? which 
developer could have left the project? 
what types of things they are doing? etc.  There is no preset 
answer here, just try to use the git commits to find information about the 
project and focus on any area you think your boss would be interested in.
In your report, write some few sentences on the git commands you found particularly useful in doing this lab.

**Name the report ```<your-names>_executive_summary.pdf>```**

Submitting the report
=======
* Put a **link to your fork repository in the report**.
* create a branch on your local fork repository called ```mining_report``` using the following command ```git branch mining_report```.
* run the command ```git checkout mining_report```
* copy your report--```<your-names>_executive_summary.pdf>``` and paste it in the folder ```repo_mining```
* push the changes onto your remote fork repository
* open a pull request and write an appropriate title and body.
* one of the repository maintainers should integrate your contribution into the main branch.
* You should also submit your report on **Canvas**

