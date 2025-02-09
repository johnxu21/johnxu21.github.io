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


## **Introduction**
This **Continuous Integration (CI) Lab** builds upon the work done in the **Testing Lab**. In this lab, you will extend the testing process by **enhancing existing test cases** with additional assertions and integrating **GitHub Actions** to automate test execution.  

CI ensures that all code changes are **continuously tested** and **validated** before being merged into the repository. You will work collaboratively, submitting **Pull Requests (PRs)** to incorporate your modifications while ensuring the test suite runs successfully in an **automated CI pipeline**.

## **Learning Outcomes**
By completing this lab, you will be able to:

- **Set up a GitHub Actions workflow** for Continuous Integration (CI).  
- **Automate test execution** for your repository using GitHub Actions.  
- **Enforce code quality** with Flake8 for Python linting.  
- **Extend test coverage** by adding meaningful assertions to existing tests.  
- **Resolve merge conflicts** and collaborate efficiently using GitHub.  
- **Submit a Pull Request (PR)** and ensure tests run successfully in CI.  

## **Repository Setup**
To begin, create a folder named `ci_lab` in your local copy of the team repository. Then, download the **starter files** from the [CI Lab repository](https://github.com/UNLV-CS472-672/CI) and copy them into the `ci_lab` folder.

- Make sure you create or copy the `.gitignore` file from the [CI Lab repository](https://github.com/UNLV-CS472-672/CI) in your repository to prevent committing unnecessary files like `.pyc`, `__pycache__/`, and environment-specific files.

## **Step 1: Setting Up GitHub Actions for Continuous Integration (CI)**

### **Overview**
In this step, you will create a **GitHub Actions workflow** to automatically **run tests and enforce code quality checks** whenever changes are pushed to the repository.

GitHub Actions enables automation for:
- Running unit tests on every **push** and **pull request**.  
- Checking for **code style violations** using **Flake8**.  
- Ensuring all test cases pass before merging changes.  


### **1. Creating a GitHub Actions Workflow File**
Good news, the workflow file is already written for you. Your task is to move it to the right location.

- Navigate to the **root directory** of your repository.
- Create the **workflow directory**:

```bash
mkdir -p .github/workflows
```
- Copy the **ci.yaml** fall from the CI_Lab directory workflow configuration file:

```bash
cd ci_lab/ci.yml .github/workflows/
```
<!-- - Open the `ci.yml` file and add the following initial setup:

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
``` -->
### **2. Understanding the Workflow**
- **Triggers:** This workflow runs **on every push** and **pull request** to the `main` branch.
- **Job Name:** The job is named **`build`**, which runs on an **Ubuntu environment**.
- **Checkout Code:** The first step **checks out** the repository so the CI workflow has access to the files.
- **Set Up Python:** Ensures the workflow uses Python 3.9.
- **Install Dependencies:** Installs the required packages listed in `requirements.txt`.
- **Run Tests with Pytest:** Executes all unit tests and generates a coverage report.
- **Install Flake8**: Ensures that Flake8 is available in the CI environment.
- **Run Flake8 Linting**: Checks for:
  - **Syntax errors** (`E9`)
  - ⚠**Undefined names** (`F63`, `F7`, `F82`)
  - **General code style issues**

### **3. Commit and Push the Changes:**
#### **a. Create a new branch** 
Create a new branch for your changes:
   ```bash
   git checkout -b add-ci-workflow
   ```
#### **b. Commit and Push the Workflow File**
If you haven't already, commit and push your CI-Lab files and ci.yml file:
```bash
git add ci_lab/
git add .github/workflows/ci.yml
git commit -m "Added initial GitHub Actions workflow"
git push origin add-ci-workflow
```

<!-- ### 3. Preventing Merge Conflicts in `ci.yml`
Since all students will be adding a GitHub Actions workflow, follow these steps to **avoid merge conflicts**:

#### **a. Sync Your Fork with the Team Repository**
Before making any changes, **ensure your fork is up to date** with the team repository:  

##### **If You Haven't Added the Team Repository as a Remote Yet**
First, add the **team repository** as an upstream remote (only needed once):
```bash
git remote add upstream <your team repo>.git
git checkout main
git fetch upstream
git merge upstream/main
```
- After syncing, update your forked repository:
```bash
git push origin main 
```

#### **b. Create a new branch** before making changes:
After syncing, create a new branch for your changes:
   ```bash
   git checkout -b add-ci-workflow
   ```
#### **c. Commit and Push the Workflow File**
If you haven't already, commit and push your ci.yml file:
```bash
git add .github/workflows/ci.yml
git commit -m "Added initial GitHub Actions workflow"
git push origin add-ci-workflow
``` -->
### **4. Check Your CI Workflow**
a) Go to your **GitHub repository**.
b) Click on the **"Actions"** tab.
c) You should see your **CI Workflow** listed.
d) If successful, you should see a **green checkmark** indicating the workflow has run successfully.
e) **If you see an error:**
   - Click on the failed workflow run to view the error logs.
   - Read the logs carefully to identify what went wrong.
   - Common issues and fixes:
     - **YAML Syntax Error:** Ensure proper indentation and correct formatting in `.github/workflows/ci.yml`.
     - **Invalid GitHub Actions Version:** Check if you're using the latest version (`actions/checkout@v3`).
     - **File Not Found:** Ensure your repository has the correct structure and files in place.
   - If you're stuck, ask for help in the **CI Discord channel**

#### **d. Open a Pull Request (PR)**  
- Open a PR from your `add-ci-workflow` branch to the **team repository (`upstream/main`)**.  
- Add a **descriptive title and summary**.  
- **Do not merge immediately**—wait for CI tests to run.  

<!-- ### **4. Check Your CI Workflow**
a) Go to your **GitHub repository**.
b) Click on the **"Actions"** tab.
c) You should see your **CI Workflow** listed.
d) If successful, you should see a **green checkmark** indicating the workflow has run successfully.
e) **If you see an error:**
   - Click on the failed workflow run to view the error logs.
   - Read the logs carefully to identify what went wrong.
   - Common issues and fixes:
     - **YAML Syntax Error:** Ensure proper indentation and correct formatting in `.github/workflows/ci.yml`.
     - **Invalid GitHub Actions Version:** Check if you're using the latest version (`actions/checkout@v3`).
     - **File Not Found:** Ensure your repository has the correct structure and files in place.
   - If you're stuck, ask for help in the **CI Discord channel** -->

<!-- ### **5. Merging PRs Without Conflicts**
To prevent merge conflicts:
- Merge **one PR at a time**—coordinate with your team.  
- Before modifying `ci.yml`, always pull the latest version of `main` from the **team repository**:  

```bash
git checkout main
git fetch upstream
git merge upstream/main
git push origin main
```
- After pulling the latest version, switch back to your feature branch:
```bash
git checkout add-ci-workflow
git merge main
```
- Resolve any merge conflicts locally before pushing again. -->

<!-- ### **. Handling Merge Conflicts**
If you encounter a merge conflict in `ci.yml`:
1. Git will mark conflicting lines. Open `ci.yml` and manually resolve the differences.  
2. After resolving conflicts, add and commit the changes:  

```bash
git add .github/workflows/ci.yml
git commit -m "Resolved merge conflict in ci.yml"
git push origin add-ci-workflow
``` -->

<!-- ## **Step 2: Installing Dependencies & Running Tests in CI**
Now that your GitHub Actions workflow is set up, the next step is to install dependencies, run test cases automatically, and enforce code quality checks.
### 1. Update the GitHub Actions Workflow (`ci.yml`)
Modify your `.github/workflows/ci.yml` file to include steps for installing dependencies and running tests.

```yaml
      - name: Set Up Python
        uses: actions/setup-python@v4
        with:
          python-version: "3.9"  # Ensure consistency in Python version

      - name: Install Dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run Tests with Pytest
        run: pytest --cov=src --cov-report=term-missing
```

### **2. Understanding the New Workflow Steps**
- **Set Up Python:** Ensures the workflow uses Python 3.9.
- **Install Dependencies:** Installs the required packages listed in `requirements.txt`.
- **Run Tests with Pytest:** Executes all unit tests and generates a coverage report. -->

<!-- ### **3. Commit and Push the Changes**
After modifying the `ci.yml` file, commit and push your changes:

```bash
git add .github/workflows/ci.yml
git commit -m "Added test execution to CI workflow"
git push origin main
``` -->

### **4. Verify Your Tests Run in CI**
- Go to your **GitHub repository**.
- Click on the **"Actions"** tab and select the latest workflow run.
- **If successful, you should see output similar to:**

```diff
==================== test session starts ====================
collected X items
... (list of passing tests)
================== coverage report ===================
```

- **If Errors Occur:**
- Click on the **failed workflow run** in the **"Actions"** tab.
- Check the **error logs** to identify the issue.
- Ensure all dependencies are correctly installed in `requirements.txt`.
- Fix any **failing tests** and push the changes:

```bash
git add .
git commit -m "Fixed failing tests"
git push origin main
```
<!-- ## **Step 3: Enforcing Code Quality with Flake8**
Now that your tests are running in the CI workflow, the next step is to **enforce Python code style and quality checks** using **Flake8**.

### **1. Updating the Workflow to Include Flake8**
Modify your `.github/workflows/ci.yml` file to add a **linting step**:

```yaml
  - name: Install Flake8
    run: pip install flake8

  - name: Run Flake8 Linting
    run: flake8 src --count --select=E9,F63,F7,F82 --show-source --statistics
```

### **2. Understanding the Linting Step**
- **Install Flake8**: Ensures that Flake8 is available in the CI environment.
- **Run Flake8 Linting**: Checks for:
  - **Syntax errors** (`E9`)
  - ⚠**Undefined names** (`F63`, `F7`, `F82`)
  - **General code style issues**

### **3. Commit and Push the Changes**
After adding the Flake8 linting step, commit and push your changes:

```bash
git add .github/workflows/ci.yml
git commit -m "Added Flake8 linting to CI workflow"
git push origin main
``` -->

### **5. Verify Linting in GitHub Actions**
1. Go to your **GitHub repository**.
2. Click on the **"Actions"** tab and select the latest workflow run.
3. **If successful**, the workflow will complete without issues.
4. **If errors occur**, Flake8 will list the violations. Fix them and push the changes.

<!-- ```bash
# Example: Fix Flake8 issues, then commit and push
git add .
git commit -m "Fixed Flake8 linting errors"
git push origin main
``` -->

## **Step 2: Writing & Automating Your Test Case in CI**

Now that you have successfully configured **Continuous Integration (CI) with GitHub Actions**, your next task is to **extend test coverage** by adding new test cases that will be automatically executed in CI.

## **Extending CI: Adding Assertions to Existing Tests**
Now that you have successfully configured **Continuous Integration (CI) with GitHub Actions**, your next step is to **collaborate with your team** to extend test coverage by **adding new assertions** to existing test cases.

### What You Will Do  
Each student will **modify one test case** in `tests/test_counter.py` by adding **one meaningful assertion**.  
This helps improve test coverage and ensures our **CI workflow** runs effectively.  

### **Key Points to Remember**
- You **do NOT** need to modify `counter.py` — the API is already implemented.  
- All test cases are written — your task is to add assertions to improve validation.  
- You must submit a Pull Request with your changes.  
- Work collaboratively — resolve merge conflicts.

### Finding Your Assigned Task
Each student has been assigned a specific assertion to add in the `tests/test_counter.py` file.  
Your assigned test case is already labeled in the file with:

- A label such as "Student 1", "Student 2", etc.  
- A description of the test case  
- A `TODO` comment specifying the assertion you need to add  
- Coordinate within your group to decide which student takes each labeled task. 
- Submit a PR to integrate your modification into the team repository

### **What to Include in Your Report**

#### ** Continuous Integration (CI) Lab Results**
- A link to your **Pull Request (PR)** for the CI Lab.
- A **copy of the assertion** you added to your assigned test case.
- A **brief explanation** of what your assertion does and how it improves test quality.
- A **summary of the CI results**, including:
  - Whether your test passed after the modification.
  - Any CI failures and how you fixed them.
  - Any additional improvements or refactoring needed.

### **Submission Instructions**
- Ensure your report is **clear and self-contained**, so it can be understood **without running your code**.  
- Upload your final report as a **PDF on Canvas**.