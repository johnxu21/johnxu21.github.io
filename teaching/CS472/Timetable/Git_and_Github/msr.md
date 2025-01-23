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


### **This individual assignment is due Jan 29th, 2025**

For this lab, you will be learning how to explore an open 
source repository from GitHub. You will also learn how to extract useful 
information from the repository and practice your project management skills by 
writing a short executive summary on your findings. 
(This assignment assumes you have installed git on your computer.  
If you haven't done this yet look at the Pro Git book or online for help.)

Important Note
======

This is an individual assignment; however, you will practice submitting your work to the team repository once groups are formed. While waiting to be assigned to a group, you can begin working on **Part 2** and **Part 3** of the assignment. These sections do not require the team repository and focus on adapting scripts, analyzing repository data, and preparing an executive summary. Once your groups are formed, you can proceed with Part 1 and practice collaborative repository management.

### **Part 1. Set Up Your Team Repository and Add Files (5 pts)**  

1. **Create a Team Repository:**  
   - One team member should create a **new GitHub repository** using your group name (e.g., `Group-1`, `Group-2`, etc.) as the repository name. Add all team members as **collaborators** to the repository.  
   - The team member who creates the repository should not push directly to the main branch. Instead, they should:  
     - Create a new branch for their changes.  
     - Make their updates on the branch.  
     - Open a pull request to merge the branch into the main branch.  

2. **Fork the Repository:**  
   - All other team members should **fork** the repository into their own GitHub accounts and then clone their fork onto their local machines.  

3. **Add the `contributors.txt` File:**  
   - The repository should include a file named `contributors.txt` to track the contributor list for your team.  

4. **Invite Me and the TA as Collaborators:**  
   - Add the following GitHub IDs as collaborators on your repository:  
     - My GitHub ID: [**`johnxu21`**](https://github.com/johnxu21)  
     - TA GitHub ID: [**`danielogen`**](https://github.com/danielogen)  

5. **Update and Commit Your Contribution:**  
   - Create a new branch called `contributors` and switch to it:  
     ```bash
     git branch contributors
     git checkout contributors
     ```  
   - Edit the `contributors.txt` file and add your **name** and **email address**.  
   - Commit your changes and push them:  
     ```bash
     git add contributors.txt
     git commit -m "Added my name and email to contributors.txt"
     git push
     ```  

6. **Submit a Pull Request:**  
   - The repository creator should create a pull request from their branch to the main branch.  
   - Team members who forked the repository should create a pull request to merge changes from their fork into the team repository. 
   - If there are any conflicts, resolve them collaboratively before merging the pull request.  


### **Part 2. Add a new file to the repository (20 pts) **
**This part of the assignment mainly contains the individual part of the assignment. 
You are supposed to modify ```CollectFiles.py``` file so that you can extract information from the repository.
As soon as the team project is created, you will work on the team part of the assignment.**

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
the authors and the dates when they touched each file in the list of files generated by the 
adapted file CollectFiles.py (only source files - **feel free to define what your source files and give your reasoning in the report**).
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

**0 weeks-means the file was touched in the early days of the project lifetime and 250 weeks means the file was touched in the 250th week of the project lifetime.**

### **Part 3. Executive Summary (5 pts)**
**This section also contains the individual part of the assignment**

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

