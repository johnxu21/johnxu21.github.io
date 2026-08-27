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

## **Lab Overview**

In this lab, you will practice Git and GitHub through a fork-based workflow that models inner-source and open-source development. You will also mine and visualize repository activity and summarize your findings in a professional report.

The lab has three parts, worth **30 points** in total:

| Part | Focus | Points |
|------|-------|--------|
| Part 1 | Practice the fork-based contribution workflow | 5 |
| Part 2 | Mine and analyze repository activity | 20 |
| Part 3 | Executive summary | 5 |

## **Learning Objectives**

By completing this lab, you should be able to:

- Apply an issue-to-merge workflow using forks, branches, commits, pull requests, and reviews.
- Synchronize repositories and resolve merge conflicts when they occur.
- Review a teammate's contribution and respond to feedback.
- Securely mine and classify repository activity.
- Visualize, interpret, and communicate repository findings.

## **Prerequisites**

- Git installed and configured
- An active GitHub account
- Basic familiarity with the command line
- Python 3 with `matplotlib` installed (needed for Parts 2 and 3)

If you need a Git refresher, consult the [Pro Git book](https://git-scm.com/book/en/v2).

## **What You Do Alone and What You Do With Your Team**

You write and submit all of the work yourself. Your team supplies the shared repository you contribute to and the teammate who reviews your pull request.

You do not have to wait for your team to be formed to start. Before your team repository exists, you can clone the [johnxu21/msrLab](https://github.com/johnxu21/msrLab) starter repository in a separate location, study and adapt its scripts, analyze the Rootbeer repository, generate the visualization, and draft the executive summary.

Once your team repository is available, create or claim your issues, create your branches, and add your finished Part 2 and Part 3 files to it as described below.

## **Team Roles and Review Rotation**

One team member serves as the **repository owner**. The owner creates the team repository, configures it, and adds the first version of `contributors.txt`. The owner works directly in the team repository; every other member works through a personal fork of it.

Before anyone opens a pull request, the team agrees on a **round-robin review rotation**. For example:

- Student 1 reviews Student 2.
- Student 2 reviews Student 3.
- Student 3 reviews Student 4.
- Continue until the last student reviews Student 1.

Use the same rotation for the Part 1 pull request and for the combined Part 2 and Part 3 pull request, unless the team agrees on another rotation that gives everyone one review to give and one to receive. The student assigned to review the repository owner also reviews the owner's initial `setup-contributors` pull request.

## **Rules for Every Pull Request in This Lab**

These rules apply to all three parts. They are stated once here and are not repeated for each pull request.

- **No direct pushes to `main`.** The only exception is the commit GitHub creates when the repository is initialized.
- Every pull request (PR) must **link to its issue** using a closing keyword, such as `Closes #12`.
- Every PR must be **approved by one teammate** before it is merged.
- All review conversations must be **resolved** before the merge.
- After approval, the **author merges their own PR**. Authors must not merge before receiving approval.
- If a reviewer requests changes, **push new commits to the same branch**. The existing PR updates automatically; do not open a second PR.

## **Collaboration Deadlines and Non-Blocking Policy**

Collaborative work creates dependencies between team members. Complete your contribution early enough for another student to review it and for you to address any requested changes.

Unless otherwise stated:

- Your PR must be complete and ready for review at least **24 hours before the assignment deadline**. A review-ready PR contains the required work, links to its issue, and is not marked as a draft.
- Assigned reviewers should complete their reviews promptly, and no later than the assignment deadline.
- The rotation names the *initial* reviewer, but reviews are not exclusive. If the assigned reviewer is unavailable, any other teammate may review and approve the PR.
- If the teammate you were assigned to review has not opened a review-ready PR, review another teammate's PR instead and submit that link on Canvas.
- If your assigned reviewer does not respond, request a review from another teammate. Do not wait.
- Notify the instructor or TA before the deadline if no teammate is available to review your work.

GitHub timestamps will be used to distinguish work completed on time from delays caused by another team member. A student who opens a complete, review-ready PR on time and makes a reasonable effort to obtain a review will not be penalized because another student submitted late or failed to complete an assigned review. Students who submit late remain responsible for obtaining the required review, and no one is required to delay their own work to accommodate a late contribution.

This policy also applies to the **Testing and Continuous Integration Lab** and to subsequent work on the **team project**. Communicate dependencies early, review teammates' work promptly, and do not allow unfinished or unreviewed work to block the team.

### **Part 1. Practice the Fork-Based Contribution Workflow (5 pts)**

#### **Purpose of This Exercise**

The change in this exercise—adding your name to `contributors.txt`—is intentionally small. The purpose is to practice the complete contribution workflow before applying it to larger programming tasks:

**Issue → Fork → Clone → Branch → Commit → Push → Pull Request → Review → Revision → Merge**

In a real project, an issue may describe a feature, bug, test, or documentation task, and the review would examine technical correctness. In this exercise, the issue and the review focus on formatting, accuracy, the scope of the change, and correct use of the GitHub workflow.

#### **Step 1. Create and Configure the Team Repository**

*This step is performed by the repository owner only. Everyone else starts at Step 2.*

##### **Create the Repository**

- Create a **public** repository so that team members can fork it. Give it a clear name, such as `Group-1`.
- Initialize the repository with a `README.md`.
- Add all team members as collaborators.
- Add the instructor and TA as collaborators:
  - Instructor: [**`johnxu21`**](https://github.com/johnxu21)
  - TA: [**`danielogen`**](https://github.com/danielogen)

##### **Protect the `main` Branch**

Create a branch protection rule for `main` *before* team members begin contributing. On GitHub, open the team repository and navigate to:

**Settings → Branches → Add branch protection rule**

Use `main` as the branch name pattern and enable:

- **Require a pull request before merging**
- **Require approvals**, set to **1** approval
- **Dismiss stale pull request approvals when new commits are pushed**
- **Require conversation resolution before merging**
- **Do not allow bypassing the above settings**, if this option is available

Do not require status checks yet; those are introduced in the Testing and Continuous Integration Lab.

These rules enforce the pull request rules listed above. For additional guidance, see the [GitHub documentation on managing branch protection rules](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/managing-a-branch-protection-rule).

> **Note:** If branch protection is unavailable for your repository or GitHub plan, the team must still follow the same requirements manually: no direct pushes to `main`, one teammate approval before merging, and all review comments resolved.

##### **Create the Initial Contributor File**

Clone the team repository:

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

Open a pull request from `setup-contributors` into `main`, and have the assigned teammate review and approve it before you merge.

#### **Step 2. Fork and Clone the Team Repository**

*Wait until `contributors.txt` has been merged into `main`.*

The repository owner skips the fork and works in the clone created in Step 1; for the owner, `origin` is the team repository.

Everyone else forks the team repository on GitHub, then clones **their own fork**, not the team repository:

```bash
git clone <URL-of-your-fork>
cd <repository-name>
```

Add the team repository as the `upstream` remote:

```bash
git remote add upstream <URL-of-team-repository>
git remote -v
```

You should now have two remotes:

- `origin`: your GitHub fork
- `upstream`: the team repository

#### **Step 3. Create or Claim an Issue**

Each student creates, or is assigned, an issue for adding their own information to `contributors.txt`.

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

Replace the example name and username with your own. This issue exists so you can practice issue-based development; in the team project, issues will describe more substantial features, bugs, tests, and documentation tasks.

#### **Step 4. Synchronize and Create a Branch**

If you are working from a fork, update your local `main` from the team repository:

```bash
git switch main
git fetch upstream
git merge upstream/main
git push origin main
```

If you are the repository owner, update your local `main` from `origin`:

```bash
git switch main
git pull origin main
```

Then create a uniquely named branch:

```bash
git switch -c contributors-<github-username>
```

For example:

```bash
git switch -c contributors-janedoe
```

#### **Step 5. Make and Push the Contribution**

Add your name and GitHub username to `contributors.txt`, keeping the table format and the alphabetical ordering by last name. Then commit and push, substituting your own name and username:

```bash
git add contributors.txt
git commit -m "Add Jane Doe to contributor list"
git push -u origin contributors-janedoe
```

#### **Step 6. Open a Pull Request**

Open a pull request into the team repository's `main` branch. If you are working from a fork, GitHub will offer to open the PR across repositories; the repository owner opens it from a branch in the team repository itself.

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

#### **Step 7. Review a Teammate's Pull Request**

Review the PR of the teammate assigned to you by the round-robin rotation. Check that:

- The PR is linked to the correct issue.
- The name and GitHub username are accurate.
- The entry follows the required table format.
- The entries remain alphabetically ordered.
- No email address or sensitive information is included.
- No unrelated files were changed.
- No unresolved conflict markers are present.

Examples of useful review comments:

```text
Please move your entry below Smith so that the list remains alphabetically ordered.
```

```text
Please remove the email address. The contributor list should contain only names and GitHub usernames.
```

```text
The PR also changes README.md, but that change is unrelated to this issue. Please revert it.
```

If the contribution satisfies all requirements, approve it and state what you verified:

```text
Approved. I verified the issue link, contributor information, table format, alphabetical ordering, and scope of the change.
```

#### **Step 8. Address Feedback and Resolve Conflicts**

If your reviewer requests changes, commit the revision to the same branch and push again; the open PR updates itself.

Because several teammates edit the same file, your branch may conflict with changes already merged into `main`. Update your branch from the team repository before resolving.

If you are working from a fork:

```bash
git fetch upstream
git switch contributors-<github-username>
git merge upstream/main
```

If you are the repository owner, your `origin` *is* the team repository:

```bash
git fetch origin
git switch contributors-<github-username>
git merge origin/main
```

Resolve the conflict in `contributors.txt` by preserving every valid entry and deleting the conflict markers. Then commit and push the resolution:

```bash
git add contributors.txt
git commit -m "Resolve contributor list conflict"
git push origin contributors-<github-username>
```

Once the reviewer confirms that the requested changes and conflicts are resolved, they approve the PR and you merge it into `main`.

#### **Part 1 Grading**

- Repository, fork, clone, and remotes configured correctly: **1 point**
- Issue created with appropriate acceptance criteria: **1 point**
- Branch, commit, and push completed correctly: **1 point**
- Pull request linked to the issue: **1 point**
- Teammate's PR reviewed with evidence-based feedback, and any feedback received on your own PR addressed: **1 point**


### **Part 2. Mine and Analyze Repository Activity (20 pts)**

#### **Purpose**

In this individual exercise, you will analyze how developers have changed an open-source repository over time. You will adapt a starter script, collect file and contributor activity, and visualize the results.

Use the same workflow you practiced in Part 1: create or claim an issue, work on a uniquely named branch, make focused commits, and push to your own GitHub repository (your fork, or the team repository if you are the owner). You will keep working on that one branch through Part 3, and open a **single** pull request covering Parts 2 and 3 at the end of Part 3.

#### **Step 1. Create or Claim an Issue**

Create or claim one issue covering both the repository analysis and the executive summary. For example:

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

Replace the example name with your own.

#### **Step 2. Create Your Branch**

Synchronize your local `main` as in Part 1, Step 4, then create your branch:

```bash
git switch -c repo-mining-<github-username>
```

#### **Step 3. Set Up the `repo_mining` Directory**

Create a directory named `repo_mining` at the root of your local clone. All Part 2 and Part 3 files go in this directory.

In a **separate location outside your clone**, clone the starter repository [johnxu21/msrLab](https://github.com/johnxu21/msrLab), and copy `CollectFiles.py` from its `src` directory into `repo_mining`. Do not clone `msrLab` inside your team repository, and do not commit the `msrLab` repository itself.

Rename the copied file to `<github-username>_collect_files.py`, for example `janedoe_collect_files.py`.

#### **Step 4. Protect Your GitHub Credentials**

The starter script uses the GitHub API. Generate a personal access token with only the permissions required to read public repository data.

Do not store the token in your Python file. Your program should read it from an environment variable or prompt for it securely at runtime. Never include a token in:

- Source code
- Commit history
- Pull request descriptions
- Screenshots
- Reports

Before committing, inspect your changes (`git diff --staged`) and confirm that no credentials are present. If you commit a token by accident, revoke it immediately and generate a new one.

See the [GitHub documentation on managing personal access tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

#### **Task 1: Identify Source Files**

Adapt `<github-username>_collect_files.py` to collect only the source files of the [scottyab/rootbeer](https://github.com/scottyab/rootbeer) repository.

A repository may contain source code, tests, documentation, configuration files, generated files, compiled files, images, and other artifacts. You decide which of these qualify as source files for this analysis.

Your solution should:

- Identify the programming languages used in the repository.
- Include the appropriate source-file extensions.
- Exclude non-source, generated, and compiled files where appropriate.
- Determine the repository's default branch rather than assuming it is named `main`.
- Produce a list of the source files selected for analysis.

In your pull request description, state your definition of a source file, justify it, and name one limitation of your selection criteria.

#### **Task 2: Collect Author and File-Touch Data**

Create a second script named `<github-username>_authors_file_touches.py`.

For each source file identified in Task 1, collect:

- File path
- Authors who changed the file
- Dates of the changes
- Number of times the file was changed

#### **Task 3: Visualize Repository Activity**

Create a third script named `<github-username>_scatterplot.py` that uses `matplotlib` to produce a scatter plot with:

- **X-axis:** weeks since the beginning of the repository
- **Y-axis:** source files
- **Color:** the author responsible for the change

Each point represents one author changing one source file during one week. The visualization should help identify frequently changed files, contributor expertise, recent activity, and possible maintenance or refactoring concerns.

Save the visualization as `<github-username>_file_activity.png`.

A related scatter-plot example is available on [Stack Overflow](https://stackoverflow.com/questions/8202605/matplotlib-scatterplot-color-as-a-function-of-a-third-variable).

##### **Example Output**

The plot below was generated from an earlier snapshot of the [scottyab/rootbeer](https://github.com/scottyab/rootbeer) repository. Your results will differ because the repository has changed since then.

Week `0` is the beginning of the repository, and larger values are later in its lifetime. Each color is a contributor, and several points in the same row mean that a file was changed many times.

<img src="/teaching/CS472/Timetable/Git_and_Github/rootbeer.jpeg" alt="Example scatter plot of Rootbeer repository activity" style="width:600px;height:480px;" align="center">

#### **Part 2 Deliverables**

Commit your work to `repo-mining-<github-username>` and push the branch. At the end of Part 2, `repo_mining` should contain:

- `<github-username>_collect_files.py`
- `<github-username>_authors_file_touches.py`
- `<github-username>_scatterplot.py`
- `<github-username>_file_activity.png`

Do not open a pull request yet. You will add the Part 3 executive summary to the same branch first.

#### **Part 2 Grading**

- Source-file collection and justified selection criteria: **5 points**
- Author and file-touch data collection: **5 points**
- Scatter-plot implementation and visualization: **5 points**
- Correct output and interpretation: **3 points**
- Repository organization, focused commits, and secure credential handling: **2 points**



### **Part 3. Executive Summary (5 pts)**

#### **Purpose**

Assume that you are a project manager preparing a status report on the [scottyab/rootbeer](https://github.com/scottyab/rootbeer) repository for a senior manager.

Your audience has limited time, so the executive summary must communicate the most important findings clearly and concisely. The report may be shared with other organizational leaders, so it should be professional, evidence-based, and understandable to a reader who has not examined the repository.

#### **Report Requirements**

Limit the executive summary to **one page**, with readable text, appropriate headings, and at least one relevant visualization.

Use the data you collected in Part 2. Depending on your results, you might address questions such as:

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

Name the report `<github-username>_executive_summary.pdf` and save it in `repo_mining` on the same branch you used for Part 2.

#### **Submit Parts 2 and 3**

Commit the executive summary and push the branch. Confirm that `repo_mining` now contains all five deliverables: the three scripts, the generated visualization, and the executive summary PDF.

Then open **one** pull request from `repo-mining-<github-username>` into the team repository's `main` branch. The PR description should:

- Use a clear title and description.
- Link and close the repository-mining issue.
- List the included scripts, visualization, and report.
- Explain how to run the scripts.
- State your definition of a source file, your justification, and one limitation.
- Summarize the main findings.
- Confirm that no credentials or unrelated files are included.
- Request a review from the teammate named by the rotation.

#### **Peer Review**

Review the Parts 2 and 3 pull request of the teammate assigned to you. Check that:

- The PR is linked to the correct issue.
- All required files are included.
- The scripts run, or the author provides sufficient evidence that they run.
- The definition of a source file is reasonable and documented.
- The collected data and the visualization are consistent with each other.
- The scatter plot has clear axes, labels, and author distinctions.
- The executive summary's conclusions are supported by the data.
- No credentials or unrelated changes are included.

Leave at least one evidence-based comment. If no changes are required, explain what you verified rather than writing only "Looks good."

The author must respond to the review and address any requested changes before the reviewer approves and the author merges.

#### **Canvas Submission**

Submit the following on Canvas:

- Executive summary PDF
- Link to your Part 1 pull request
- Link to your final Parts 2 and 3 pull request
- Links to the two pull requests you reviewed: one from Part 1 and one from Parts 2 and 3
- Link to your GitHub fork, or to the team repository if you are the repository owner
- A brief reflection, entered directly in Canvas, identifying the Git commands that were particularly useful during the lab

Each pull request you submit must link to its issue and show the commits, changed files, review comments, approval, and merge status.

#### **Part 3 Grading**

- Significant findings supported by repository evidence: **2 points**
- Visualization and interpretation: **1 point**
- Clear, concise, and professional presentation: **1 point**
- Complete PR, peer review, and Canvas submission: **1 point**
