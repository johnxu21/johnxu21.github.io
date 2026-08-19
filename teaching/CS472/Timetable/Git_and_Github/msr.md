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

 <!--
  Hidden during the control-class semester.
<form action="/teaching/CS472/Timetable/LLM/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="Generative AI" />
</form>
 -->
</div>

<br/>
<br/>


### **Due Date: Sept 2, 2026**

## Lab Overview

In this lab, you will practice Git and GitHub through a fork-based workflow that models inner-source and open-source development. You will also mine and visualize repository activity and summarize your findings in a professional report.

## Learning Objectives

By completing this lab, you should be able to:
- Distinguish among an upstream repository, a GitHub fork, and a local clone.
- Create a branch, make meaningful commits, and push your changes.
- Open a pull request and participate in peer review.
- Synchronize a fork with the upstream repository and resolve merge conflicts when they occur.
- Extract, visualize, and interpret repository activity.
- Communicate findings in a concise executive summary.

## Prerequisites

You must have Git installed, an active GitHub account, and basic familiarity with the command line. If necessary, consult the [Pro Git book](https://git-scm.com/book/en/v2).

## Individual and Team Components

This is primarily an individual assignment. Before teams are formed, you may clone the starter repository in a separate location, study and adapt the scripts, analyze the Rootbeer repository, generate the visualization, and begin drafting the executive summary.

After your team repository is available, create or claim the required issue, create your repository-mining branch, and add the completed Part 2 and Part 3 files to the `repo_mining` directory in your local team-repository clone.

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

#### Protect the `main` Branch

The repository owner should create a branch protection rule for `main` before team members begin contributing.

On GitHub, open the team repository and navigate to:

**Settings → Branches → Add branch protection rule**

Use `main` as the branch name pattern and enable the following settings:

- **Require a pull request before merging**
- **Require one approval before merging**
- **Dismiss stale pull request approvals when new commits are pushed**
- **Require conversation resolution before merging**
- **Do not allow bypassing the above settings**, if this option is available

Do not require status checks yet. Automated status checks will be introduced in the testing and continuous integration labs.

These rules prevent team members from pushing changes directly to `main`. A contribution must be submitted through a pull request and approved by another team member.

After the reviewer approves the PR and all conversations and conflicts are resolved, the reviewer should ask the author to merge the PR. Because all team members are collaborators, the approved PR author may merge their own contribution.

For additional guidance, see the [GitHub documentation on managing branch protection rules](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/managing-a-branch-protection-rule).

> **Note:** If branch protection is unavailable for the repository or GitHub plan being used, the team must follow the same requirements manually: no direct pushes to `main`, one teammate approval before merging, and all review comments resolved.

#### Create the Initial Contributor File
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

#### Round-Robin Review Assignment

The team should assign reviews in a round-robin sequence (This also applies to Parts 2 and 3). For example:

- Student 1 reviews Student 2.
- Student 2 reviews Student 3.
- Student 3 reviews Student 4.
- Continue until the final student reviews Student 1.

The same assignment should be used for the Part 1 PR and the combined Part 2 and Part 3 PR unless the team agrees on another balanced rotation.

The student assigned to review the repository owner should also review the initial `setup-contributors` PR.

Reviewers should complete reviews promptly. Do not delay a teammate's submission by leaving an assigned review unfinished.

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

#### 8. Address Feedback and Resolve Conflicts When Necessary

If the reviewer requests changes, update the same branch, commit the revision, and push again. The existing PR will update automatically.

Because several team members are editing the same file, your branch may conflict with changes already merged into `main`.

**Students working through forks** should update their contribution branch from the upstream team repository:

```bash
git fetch upstream
git switch contributors-<github-username>
git merge upstream/main
```

**The repository owner** should update the contribution branch from `origin`, because the owner's `origin` is the team repository:

```bash
git fetch origin
git switch contributors-<github-username>
git merge origin/main
```

Resolve the conflict in `contributors.txt`, preserve all valid entries, and remove the conflict markers. Then commit and push the resolution:

```bash
git add contributors.txt
git commit -m "Resolve contributor list conflict"
git push origin contributors-<github-username>
```

The existing pull request will update automatically. Do not open another pull request.

After confirming that the requested changes have been addressed and any conflicts have been resolved, the reviewer should approve the pull request and ask the author to merge it into `main`. Authors must not merge their pull requests before receiving approval from a teammate.

#### Part 1 Grading

- Repository, fork, clone, and remotes configured correctly: **1 point**
- Issue created with appropriate acceptance criteria: **1 point**
- Branch, commit, and push completed correctly: **1 point**
- Pull request linked to the issue: **1 point**
- Teammate's PR reviewed with evidence-based feedback, and any feedback received on the student's own PR was addressed: **1 point**


### **Part 2. Mine and Analyze Repository Activity (20 pts)**

#### Purpose

In this individual exercise, you will analyze how developers have changed an open-source repository over time. You will adapt a starter script, collect file and contributor activity, and visualize the results.

Apply the Git and GitHub workflow practiced in Part 1. Create or claim an issue, work on a uniquely named branch, make focused commits, and push your work to your fork. You will add the Part 3 executive summary to the same branch before opening the final pull request.

A teammate will review the completed pull request containing your Part 2 and Part 3 work.

#### Set Up the Repository-Mining Task

Create a `repo_mining` directory in your local team-repository clone.

In a separate location outside the team repository, clone [johnxu21/msrLab](https://github.com/johnxu21/msrLab). Copy `CollectFiles.py` from its `src` directory into `repo_mining`.

Do not clone `msrLab` inside the team repository, and do not commit the complete `msrLab` repository.

Rename the copied file:

`<github-username>_collect_files.py`

For example:

`janedoe_collect_files.py`

#### Create or Claim an Issue

Create or claim an issue covering the repository analysis and executive summary.

Example:

```text
Title: Analyze Rootbeer repository activity for Jane Doe

Description:
Analyze file and contributor activity in the scottyab/rootbeer repository and prepare an executive summary.

Acceptance Criteria:
- The source-file collection script is included.
- The author and file-touch data are collected.
- A scatter plot of repository activity is included.
- A one-page executive summary is included.
- No credentials or unrelated files are committed.
```

Replace the example name with your own name.

#### Protect Your GitHub Credentials

The starter script uses the GitHub API. Generate a personal access token with only the permissions required to read public repository data.

Do not store the token directly in your Python file. Your program should obtain it from an environment variable or request it securely at runtime.

Never include a token in:

- Source code
- Commit history
- Pull-request descriptions
- Screenshots
- Reports

Before committing, inspect your changes and confirm that no credentials are present. If a token is accidentally committed, revoke it immediately and generate a new one.

See the [GitHub documentation on managing personal access tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

#### Task 1: Identify Source Files

Adapt `<github-username>_collect_files.py` to collect only source files from the [scottyab/rootbeer](https://github.com/scottyab/rootbeer) repository.

A repository may contain source code, tests, documentation, configuration files, generated files, images, and other artifacts. Determine which files qualify as source files for this analysis.

Your solution should:

- Identify the programming languages used in the repository.
- Include appropriate source-file extensions.
- Exclude non-source and generated files where appropriate.
- Produce a list of the source files selected for analysis.

Document and justify your definition of a source file in the Part 3 executive summary.

#### Task 2: Collect Author and File-Touch Data

Create a second script named:

`<github-username>_authors_file_touches.py`

For each source file identified in Task 1, collect:

- File path
- Authors who changed the file
- Dates of the changes
- Number of times the file was changed

#### Task 3: Visualize Repository Activity

Create a third script named:

`<github-username>_scatterplot.py`

Use `matplotlib` to create a scatter plot with:

- **X-axis:** weeks since the beginning of the repository
- **Y-axis:** source files
- **Color:** author responsible for the change

Each point should represent an author changing a source file during a particular week. The visualization should help identify frequently changed files, contributor expertise, recent activity, and possible maintenance or refactoring concerns.

Save the visualization as:

`<github-username>_file_activity.png`

A related scatter-plot example is available on [Stack Overflow](https://stackoverflow.com/questions/8202605/matplotlib-scatterplot-color-as-a-function-of-a-third-variable).

#### Example

The example below was generated from an earlier snapshot of the [scottyab/rootbeer](https://github.com/scottyab/rootbeer) repository. Your results may differ because the repository has changed.

Week `0` represents activity near the beginning of the repository. Later values represent activity later in its lifetime. Each color represents a contributor, and repeated points indicate that a file was changed multiple times.

<img src="/teaching/CS472/Timetable/Git_and_Github/rootbeer.jpeg" alt="Example scatter plot of Rootbeer repository activity" style="width:600px;height:480px;" align="center">

#### Part 2 Deliverables

Your `repo_mining` directory should contain:

- Adapted source-file collection script
- Author and file-touch collection script
- Scatter-plot script
- Generated visualization

Push the completed work to your repository-mining branch. Keep the branch open because you will add the Part 3 executive summary before opening the final pull request.

#### Part 2 Grading

- Source-file collection and justified selection criteria: **5 points**
- Author and file-touch data collection: **5 points**
- Scatter-plot implementation and visualization: **5 points**
- Correct output and interpretation: **3 points**
- Repository organization, focused commits, and secure credential handling: **2 points**



### **Part 3. Executive Summary (5 pts)**

#### Purpose

Assume that you are a project manager preparing a status report on the [scottyab/rootbeer](https://github.com/scottyab/rootbeer) repository for a senior manager.

Your audience has limited time, so the executive summary must communicate the most important findings clearly and concisely. The report may be shared with other organizational leaders; therefore, it should be professional, evidence-based, and understandable to a reader who has not examined the repository.

#### Report Requirements

Limit the executive summary to **one page** and use readable text, appropriate headings, and at least one relevant visualization.

Use the repository data collected in Part 2 to discuss the most important findings. Depending on your results, you may address questions such as:

- How much development activity has occurred, and how has it changed over time?
- Which contributors performed the most work overall?
- Which contributors have been most active recently?
- Which files changed most frequently?
- Which contributors appear to have the most experience with particular files?
- Are important files dependent on only one or two contributors?
- Are there contributors who may no longer be active?
- What maintenance or refactoring concerns are suggested by the data?

There is no single correct interpretation. Select the findings that would be most useful to a project manager and support them with evidence from the repository.

The report must include:

- A brief description of the analysis
- Two or three significant findings supported by repository data
- The scatter plot produced in Part 2
- An explanation of what the visualization shows
- At least one limitation of the analysis
- A brief reflection identifying the Git commands that were particularly useful during the lab
- Link to your GitHub fork

Name the report:

`<github-username>_executive_summary.pdf`

Save the report in your `repo_mining` directory on the same branch used for Part 2.

#### Submit Parts 2 and 3

After adding the executive summary, confirm that your branch contains:

- Adapted source-file collection script
- Author and file-touch collection script
- Scatter-plot script
- Generated visualization
- Executive summary PDF

Make a focused commit for the executive summary and push the updated branch to your fork.

Open one pull request from your repository-mining branch to the upstream team repository. The PR should:

- Use a clear title and description.
- Link and close the repository-mining issue.
- List the included scripts, visualization, and report.
- Explain how the scripts can be run.
- Summarize the main findings.
- Confirm that no credentials or unrelated files are included.
- Request a review from the assigned teammate.

#### Peer Review

Each student must review one teammate's Part 2 and Part 3 pull request.

The reviewer should check that:

- The PR is linked to the correct issue.
- All required files are included.
- The scripts run or the author provides sufficient evidence that they run.
- The definition of a source file is reasonable and documented.
- The collected data and visualization appear consistent.
- The scatter plot has clear axes, labels, and author distinctions.
- The executive summary's conclusions are supported by the data.
- No credentials or unrelated changes are included.

The reviewer should provide at least one evidence-based comment. If no changes are required, the reviewer should explain what was verified rather than writing only “Looks good.”

The author must respond to the review and address any requested changes. Once the reviewer is satisfied, the reviewer should approve the PR and ask the author to merge it into `main`. Authors must not merge their PRs before receiving approval.

#### Canvas Submission

Submit the following on Canvas:

- Executive summary PDF
- Link to your Part 1 issue and pull request
- Link to your Parts 2 and 3 issue and final pull request
- Links to the two pull requests you reviewed: one from Part 1 and one from Parts 2 and 3

Each pull request must link to its corresponding issue and show the commits, changed files, review comments, approval, and merge status.

#### Part 3 Grading

- Significant findings supported by repository evidence: **2 points**
- Visualization and interpretation: **1 point**
- Clear, concise, and professional presentation: **1 point**
- Complete PR, peer review, and Canvas submission: **1 point**

