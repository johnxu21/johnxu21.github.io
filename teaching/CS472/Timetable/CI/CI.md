---
layout: page
title: CS472 - CI - Using GitHub Actions - Setting up workflow
permalink: /teaching/CS472/Timetable/CI/
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
    <input type="submit" style="background-color:#008CBA;float:left; color:white;width:130px;
height:30px;" value="Git & GitHub" />
</form>
<form action="/teaching/CS472/Timetable/dynamic_analysis/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="Testing" />
</form>
<form action="/teaching/CS472/Timetable/CI/">
    <input type="submit" style="background-color:firebrick;float:left;color:white;width:130px;
height:30px;" value="CI" />
</form>
<!--form action="/teaching/CS472/Timetable/GPT/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="ChatGPT" />
</form-->
</div>

<br/>
<br/>

## **This individual assignment is due Feb 17th, 2025**


## **Introduction**
This **Continuous Integration (CI) Lab** builds upon the work done in the **Testing Lab**. In this lab, you will extend the testing process by **enhancing existing test cases** with additional assertions and integrating **GitHub Actions** to automate test execution.  

You will configure a CI pipeline, add tests to improve coverage, enforce code quality gates, and learn to debug failing runs. Unlike earlier labs, this is an **individual assignment**:contentReference[oaicite:1]{index=1}: each student must complete their own contributions, documented and submitted separately.

CI ensures that all code changes are **continuously tested, linted, and validated** before being merged into the repository. You will practice modern DevOps workflows using **Pull Requests (PRs)**, **Issues**, and **peer reviews**:contentReference[oaicite:2]{index=2}.

## Learning Outcomes

By completing this lab, you will be able to:

- **Set up and extend a GitHub Actions workflow** for CI.  
- **Automate test execution** across multiple Python versions.  
- **Use caching** to optimize CI runtime.  
- **Enforce code coverage thresholds** (fail if coverage < 80%).  
- **Integrate code formatting and linting** (Black + Flake8).  
- **Write and run your own unit test** in CI, and measure coverage before/after.  
- **Debug CI failures** by interpreting workflow logs.  
- **Submit focused PRs** linked to Issues and reviewed by peers.   
  
---

## Repository Setup
You will complete this lab in **your own fork** of the course repository.
1. Create a new folder named ``ci_lab`` inside your fork.  
2. Download starter files from the [CI Lab repository](https://github.com/UNLV-CS472-672/CI).  
3. Place them into `ci_lab` folder and commit them to your fork.  
4. Ensure `.gitignore` excludes unnecessary files like `.pyc`, `__pycache__/`, and environment-specific configs. 
5. Push your changes to your fork’s `main` branch.

After this setup, all of your work (Pipeline PR, Testing PR, Debugging PR) will be done in branches and PRs within your fork.

## General Rules for PRs
You will complete this lab in **your own fork** of the repository (recommended for individual grading).
- Each PR must have:
  - A **descriptive title** (e.g., “Add coverage gate to CI workflow”).  
  - A **clear PR description** including:
    - A short YAML excerpt showing the workflow change.  
    - An explanation of what the change does.  
    - A link or screenshot of the CI run showing success/failure.  
- Keep PRs **small and focused**:  
  - One enhancement per Pipeline PR.  
  - One new test in the Testing PR.  
  - One failure+fix in the Debugging PR.  

---

## Individual Tasks (3 PRs per student)

Each student must complete **three Pull Requests (PRs)**, linked to Issues, and include **before/after coverage evidence** in their PR description.  

### 1. Pipeline PR (choose ONE unique enhancement)

Each student must complete **one distinct pipeline enhancement** from the list below.  
No two students in the same team may select the same enhancement.  
Your PR must include:  
- The **YAML excerpt** showing your change.  
- At least **one new test you authored** (all PRs must include a test).  
- A short explanation of the enhancement and its effect.  

**Requirements for your Pipeline PR:**
- Focus on implementing **your assigned CI enhancement** (see list below).  
- Demonstrate that the **existing test suite runs successfully** under your new workflow (link to the CI run or screenshot).  
- Include a short **YAML excerpt** in your PR description showing the relevant workflow change.  
- Briefly explain how your enhancement improves the CI pipeline.  

#### Available Enhancements (8 total)

1. **Matrix Setup**  
   - Extend workflow to run tests on Python 3.9, 3.10, and 3.11.  
   - Evidence: CI run screenshot showing jobs for all three versions.  

2. **Dependency Caching**  
   - Use `actions/cache` to cache Python dependencies.  
   - Evidence: CI logs showing a cache hit on reruns.  

3. **Lint/Format Enforcement**  
   - Add **Flake8** (lint) and **Black** (formatter).  
   - Configure jobs to fail on violations.  
   - Evidence: CI run where lint passes (or fails and you fix it).  

4. **Coverage Gate**  
   - Enforce ≥80% coverage using `pytest --cov --cov-fail-under=80`.  
   - Evidence: CI run with coverage summary showing threshold enforced.  

5. **Coverage Artifact Upload**  
   - Configure CI to upload the full HTML/text coverage report as an artifact.  
   - Evidence: Screenshot of artifact available in the Actions tab.  

6. **Status Badges in README**  
   - Add build/lint/coverage badges to the repo `README.md`.  
   - Evidence: Updated README rendered on GitHub with badges.  

7. **Split Jobs**  
   - Separate workflow into distinct jobs: `lint`, `test`, `coverage`.  
   - Evidence: CI run showing multiple jobs instead of one monolithic job.  

8. **Notifications**  
   - Add a step to post CI status (pass/fail) as a comment on the PR.  
   - Evidence: Screenshot of CI comment automatically posted on your PR.  

---

_Note:_ If your team already has a working version of one enhancement, you may still complete that task in your own branch, but your PR must be **independent** and include your own explanation and evidence.

## 2. **One testing PR (required)**
   - Write **at least one new meaningful unit test** (your own authorship) that runs in CI.  
   - Show **coverage before vs. after** and briefly explain what behavior/edge case your test covers.  
   Your testing lab already shows how to run `pytest --cov` and read coverage output.

## 3. **One debugging PR (required)**
   - Introduce a small, controlled failure (failing test, style error, or coverage drop) on a branch.  
   - Use the **Actions logs** to diagnose, then push a fix and re‑run to green.  
   - In the PR description, paste the failing log snippet and the root‑cause + fix summary.  
   This mirrors the CI failure‑investigation flow in the CI lab steps.

> You may open these PRs **against the team repository** (preferred for collaboration/reviews) **or** work in your **fork** and include links. Either way, grading is **per‑student** via your report.

## Required sequence (per student)

1. **Sync repo** and confirm the baseline CI workflow runs (Actions tab, green check).  
2. **Write & run your own test** locally and in CI:  
   ```bash
   pytest --cov=src --cov-report=term-missing
   ```

## Individual Report

Your report is the primary artifact for grading. It must be prepared as a **PDF** and uploaded to Canvas.  

### What to include in your report:
1. **Link to your fork repository** (GitHub URL).  
2. **Links to your three PRs** in your fork (Pipeline, Testing, Debugging).  
3. **Coverage evidence**:
   - Before vs. after coverage tables for your Testing PR.  
4. **CI log evidence**:
   - A failing CI log snippet and your fix summary for the Debugging PR.  
5. **Code excerpts**:
   - Your new test function (Testing PR).  
   - YAML snippet showing your workflow change (Pipeline PR).  
6. **A paragraph explaining what you learned about CI and automated quality checks.  

---

## Submission Instructions

- Upload your final report as a **PDF on Canvas**.  
- Make sure the report is **self-contained**:
  - Do not require graders to browse your fork unless for verification.  
  - Paste or screenshot essential evidence (coverage tables, log snippets, YAML/test code) into the PDF.  
- Double-check that your **fork repository link** is correct and public.  
- Submit before the posted deadline (see course timetable).  
