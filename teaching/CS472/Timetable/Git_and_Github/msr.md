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
height:30px;" value="Testing & CI" />
</form>
<form action="/teaching/CS472/Timetable/LLM/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="Generative AI" />
</form>
</div>

<br/>
<br/>


### **Due Date: February 2, 2026**

## Lab Overview

In this lab, you will practice Git and GitHub through a fork-based workflow that models inner-source and open-source development. You will also mine and visualize repository activity and summarize your findings in a professional report.

## Learning Objectives

By completing this lab, you should be able to:
- Distinguish among an upstream repository, a GitHub fork, and a local clone.
- Create a branch, make meaningful commits, and push your changes.
- Open a pull request and participate in peer review.
- Synchronize a fork with upstream and resolve merge conflicts.
- Extract, visualize, and interpret repository activity.
- Communicate findings in a concise executive summary.

## Prerequisites

You must have Git installed, an active GitHub account, and basic familiarity with the command line. If necessary, consult the [Pro Git book](https://git-scm.com/book/en/v2).

## Individual and Team Components

This is primarily an individual assignment. You may begin **Parts 2 and 3** before teams are formed.

After teams are formed, complete **Part 1** using the team repository as the authoritative upstream repository. Except for the repository owner, each member will contribute through an individual fork. You will then submit your work from Parts 2 and 3 to the team repository using the same contribution workflow.

### **Part 1. Practice the Fork-Based Contribution Workflow (5 pts)**

#### Purpose of This Exercise

The change in this exercise—adding your name to `contributors.txt`—is intentionally small. The purpose is to practice the complete contribution workflow before applying it to larger programming tasks:

**Issue → Fork → Clone → Branch → Commit → Push → Pull Request → Review → Revision → Merge**

In a real project, an issue may describe a feature, bug, test, or documentation task, and the review would examine technical correctness. In this exercise, the issue and review focus on formatting, accuracy, the scope of the change, and correct use of the GitHub workflow.

#### 1. Create and Configure the Team Repository

One team member will serve as the repository owner and should:

- Create a GitHub repository named after the team, such as `Group-1`.
- Initialize the repository with a `README.md`.
- Add all team members as collaborators.
- Add the instructor and TA as collaborators:
  - Instructor: [**`johnxu21`**](https://github.com/johnxu21)
  - TA: [**`danielogen`**](https://github.com/danielogen)

The repository owner should clone the team repository:

```bash
git clone <URL-of-team-repository>
cd <repository-name>
```

Create and switch to a setup branch:

```bash
git switch -c setup-contributors
```

Create `contributors.txt` with the following content:

```text
Team Contributors

Name | GitHub Username
-----|----------------
```

Commit and push the file:

```bash
git add contributors.txt
git commit -m "Create contributor list"
git push -u origin setup-contributors
```

Open a pull request to merge `setup-contributors` into `main`. A teammate should review and approve the PR before it is merged.

Except for repository initialization, team members must not push directly to `main`.

#### 2. Fork and Clone the Team Repository

After `contributors.txt` has been merged, all team members except the repository owner should fork the team repository.

Clone your own fork—not the upstream team repository:

```bash
git clone <URL-of-your-fork>
cd <repository-name>
```

Add the team repository as the `upstream` remote:

```bash
git remote add upstream <URL-of-team-repository>
git remote -v
```

Your remotes should have the following purposes:

- `origin`: your GitHub fork
- `upstream`: the team repository

The repository owner does not need to create a fork. For the repository owner, `origin` refers to the team repository.

#### 3. Create or Claim an Issue

Each student should create or be assigned an issue for adding their information to `contributors.txt`.

Example issue:

```text
Title: Add Jane Doe to the contributor list

Description:
Add Jane Doe and the GitHub username janedoe to contributors.txt.

Acceptance Criteria:
- The contributor's name and GitHub username are included.
- The new entry follows the existing table format.
- Entries remain ordered alphabetically by last name.
- No email address or other personal information is included.
- No unrelated files are changed.
```

This issue is for practicing issue-based development. In the team project, issues will describe more substantial features, bugs, tests, documentation, and other development tasks.

#### 4. Synchronize and Create a Branch

Students working through forks should synchronize their local repositories before starting:

```bash
git switch main
git fetch upstream
git merge upstream/main
git push origin main
```

The repository owner should synchronize using:

```bash
git switch main
git pull origin main
```

Create a uniquely named branch:

```bash
git switch -c contributors-<github-username>
```

For example:

```bash
git switch -c contributors-janedoe
```

#### 5. Make and Push the Contribution

Add your name and GitHub username to `contributors.txt`. Maintain the table format and alphabetical ordering.

Commit and push the change:

```bash
git add contributors.txt
git commit -m "Add Jane Doe to contributor list"
git push -u origin contributors-janedoe
```

Replace the example name and username with your own information.

#### 6. Open a Pull Request

Open a pull request from your branch to the upstream repository's `main` branch.

Use the following structure:

```text
Title: Add Jane Doe to contributor list

Summary:
Adds Jane Doe and the GitHub username janedoe to contributors.txt.

Related Issue:
Closes #<issue-number>

Verification:
- Confirmed that the entry follows the required table format.
- Confirmed that the list remains alphabetically ordered.
- Confirmed that no unrelated files were changed.
```

The repository owner should open a PR from a branch in the team repository. Other members should open PRs from branches in their forks.

#### 7. Review a Teammate's Pull Request

Each student must review one teammate's PR. For this exercise, check that:

- The PR is linked to the correct issue.
- The name and GitHub username are accurate.
- The entry follows the required table format.
- The entries remain alphabetically ordered.
- No email address or sensitive information is included.
- No unrelated files were changed.
- No unresolved conflict markers are present.

Appropriate review comments include:

```text
Please move your entry below Smith so that the list remains alphabetically ordered.
```

```text
Please remove the email address. The contributor list should contain only names and GitHub usernames.
```

```text
The PR also changes README.md, but that change is unrelated to this issue. Please revert it.
```

If the contribution satisfies all requirements, the reviewer may approve it and explain what was verified:

```text
Approved. I verified the issue link, contributor information, table format, alphabetical ordering, and scope of the change.
```

#### 8. Address Feedback and Resolve Conflicts

If the reviewer requests changes, update the same branch, commit the revision, and push again. The existing PR will update automatically.

Because several team members are editing the same file, your branch may conflict with changes already merged into `main`. If this occurs, synchronize your branch:

```bash
git fetch upstream
git switch contributors-<github-username>
git merge upstream/main
```

Resolve the conflict in `contributors.txt`, preserve all valid entries, and remove the conflict markers. Then run:

```bash
git add contributors.txt
git commit -m "Resolve contributor list conflict"
git push origin contributors-<github-username>
```

A repository maintainer should merge the PR only after the review is complete, requested changes are addressed, and any conflicts are resolved.

#### Part 1 Grading

- Repository, fork, clone, and remotes configured correctly: **1 point**
- Issue created with appropriate acceptance criteria: **1 point**
- Branch, commit, and push completed correctly: **1 point**
- Pull request linked to the issue: **1 point**
- Teammate's PR reviewed and feedback addressed: **1 point**


### **Part 2. Add a new file to the repository (20 pts)**
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
This graph below was generated some time ago, so your graph is expected to be more detailed, reflecting the additional updates made to the repository since then.

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

