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
<form action="/teaching/CS472/Timetable/GPT/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="CHAT GPT" />
</form>
</div>

<br/>
<br/>

## **This individual assignment is due Feb 12th, 2025**


## **📢 Introduction**
This **Continuous Integration (CI) Lab** builds upon the work done in the **[Testing lab](../dynamic_analysis)**. In this lab, you will extend your testing process by integrating **GitHub Actions** to automate test execution and enforce code quality checks. CI ensures that code changes are **continuously tested** and **validated** before being merged into the main repository.

By the end of this lab, you will have a **fully automated CI pipeline** that runs your test suite and checks for code quality issues **whenever a change is pushed or a pull request is made**.

## ** Learning Outcomes**
By completing this lab, you will be able to:
✔️ **Set up a GitHub Actions workflow** for Continuous Integration (CI).  
✔️ **Automate test execution** for your repository using GitHub Actions.  
✔️ **Enforce code quality** with Flake8 for Python linting.  
✔️ **Extend test coverage** by adding new test cases.  
✔️ **Resolve merge conflicts** and collaborate efficiently using GitHub.
---

## **📁 Repository Setup**
To begin, download the **starter files** from the [CI Lab repository](https://github.com/UNLV-CS472-672/CI) and copy them into the local copy of your fork of the team repository.

# **🔧 Step 1: Setting Up GitHub Actions for Continuous Integration (CI)**

## **📌 Overview**
In this step, you will create a **GitHub Actions workflow** to automatically **run tests and enforce code quality checks** whenever changes are pushed to the repository.

GitHub Actions enables automation for:
- Running unit tests on every **push** and **pull request**.  
- Checking for **code style violations** using **Flake8**.  
- Ensuring all test cases pass before merging changes.  

---

## **1. Creating a GitHub Actions Workflow File**
1. Navigate to the **root directory** of your repository.
2. Create the **workflow directory**:
   ```bash
   mkdir -p .github/workflows
   ```
3. Create the workflow configuration file:
    ```bash
    touch .github/workflows/ci.yml
    ```
4. Open the `ci.yml` file and add the following initial setup:
```yaml
name: CI Workflow  # Name of the workflow

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest  # Use the latest Ubuntu runner

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v3
```
## **2. Understanding the Workflow**
- **Triggers:** This workflow runs **on every push** and **pull request** to the `main` branch.
- **Job Name:** The job is named **`build`**, which runs on an **Ubuntu environment**.
- **Checkout Code:** The first step **checks out** the repository so the CI workflow has access to the files.

## **3. Committing and Pushing the Workflow**
### **Add the workflow file to Git:**
```bash
git add .github/workflows/ci.yml
```
- Commit the changes:
```bash
git commit -m "Added initial GitHub Actions workflow"
```
- Push to the main repository:
```bash
git push origin main
```

## 4. **Check Your CI Workflow**
1. Go to your **GitHub repository**.
2. Click on the **"Actions"** tab.
3. You should see your **CI Workflow** listed.
4. If successful, you should see a **green checkmark ✅** indicating the workflow has run successfully.






