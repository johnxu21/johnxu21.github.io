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
-  **Automate test execution** for your repository using GitHub Actions.  
-  **Enforce code quality** with Flake8 for Python linting.  
-  **Extend test coverage** by adding new test cases.  
-  **Resolve merge conflicts** and collaborate efficiently using GitHub.


## ** By the end of this lab, you will:**
- Add **meaningful assertions** to enhance existing test cases.  
- Submit a **Pull Request (PR)** to integrate your changes.  
- Ensure your tests **run successfully** in the CI workflow.  
- Collaborate effectively using GitHub.

## ** Repository Setup**
To begin, download the **starter files** from the [CI Lab repository](https://github.com/UNLV-CS472-672/CI) and copy them into the local copy of your fork of the team repository.

- Make sure to copy create or copy the `.gitignore` file from the [CI Lab repository](https://github.com/UNLV-CS472-672/CI) in your repository to prevent committing unnecessary files like `.pyc`, `__pycache__/`, and environment-specific files.

# **Step 1: Setting Up GitHub Actions for Continuous Integration (CI)**

## ** Overview**
In this step, you will create a **GitHub Actions workflow** to automatically **run tests and enforce code quality checks** whenever changes are pushed to the repository.

GitHub Actions enables automation for:
- Running unit tests on every **push** and **pull request**.  
- Checking for **code style violations** using **Flake8**.  
- Ensuring all test cases pass before merging changes.  


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
4. If successful, you should see a **green checkmark** indicating the workflow has run successfully.
5. **If you see an error:**
   - Click on the failed workflow run to view the error logs.
   - Read the logs carefully to identify what went wrong.
   - Common issues and fixes:
     - **YAML Syntax Error:** Ensure proper indentation and correct formatting in `.github/workflows/ci.yml`.
     - **Invalid GitHub Actions Version:** Check if you're using the latest version (`actions/checkout@v3`).
     - **File Not Found:** Ensure your repository has the correct structure and files in place.
   - If you're stuck, ask for help in the **CI Discord channel**

## **Installing Dependencies & Running Tests in CI**
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
- **Run Tests with Pytest:** Executes all unit tests and generates a coverage report.

### **3. Commit and Push the Changes**
After modifying the `ci.yml` file, commit and push your changes:

```bash
git add .github/workflows/ci.yml
git commit -m "Added test execution to CI workflow"
git push origin main
```

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
## **Next Step: Enforcing Code Quality with Flake8**
Now that your tests are running in the CI workflow, the next step is to **enforce Python code style and quality checks** using **Flake8**.

### **1. Updating the Workflow to Include Flake8**
Modify your `.github/workflows/ci.yml` file to add a **linting step**:

```yaml
  - name: Install Flake8
    run: pip install flake8

  - name: Run Flake8 Linting
    run: flake8 src --count --select=E9,F63,F7,F82 --show-source --statistics
```

## **2. Understanding the Linting Step**
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
```

### **4. Verify Linting in GitHub Actions**
1. Go to your **GitHub repository**.
2. Click on the **"Actions"** tab and select the latest workflow run.
3. **If successful**, the workflow will complete without issues.
4. **If errors occur**, Flake8 will list the violations. Fix them and push the changes.

```bash
# Example: Fix Flake8 issues, then commit and push
git add .
git commit -m "Fixed Flake8 linting errors"
git push origin main
```

# **Writing & Automating Your Test Case in CI**

Now that you have successfully configured **Continuous Integration (CI) with GitHub Actions**, your next task is to **extend test coverage** by adding new test cases that will be automatically executed in CI.

# **Extending CI: Adding Assertions to Existing Tests**
Now that you have successfully configured **Continuous Integration (CI) with GitHub Actions**, your next step is to **collaborate with your team** to extend test coverage by **adding new assertions** to existing test cases.

## What You Will Do  
Each student will **modify one test case** in `tests/test_counter.py` by adding **one meaningful assertion**.  
This helps improve test coverage and ensures our **CI workflow** runs effectively.  

## **Key Points to Remember**
- You do NOT need to modify `counter.py` —the API is already implemented.  
- All test cases are written — your task is to add assertions to improve validation.  
- You must submit a Pull Request with your changes.  
- Work collaboratively — resolve merge conflicts.

## Finding Your Assigned Task
Each student has been assigned a specific assertion to add in the `tests/test_counter.py` file.  
Your assigned test case is already labeled in the file with:

- A label such as "Student 1", "Student 2", etc.  
- A description of the test case  
- A `TODO` comment specifying the assertion you need to add  
- Coordinate within your group to decide which student takes each labeled task. 
- Submit a PR to integrate your modification into the team repository

## **What to Include in Your Report**

### ** Continuous Integration (CI) Lab Results**
- A link to your **Pull Request (PR)** for the CI Lab.
- A **copy of the assertion** you added to your assigned test case.
- A **brief explanation** of what your assertion does and how it improves test quality.
- A **summary of the CI results**, including:
  - Whether your test passed after the modification.
  - Any CI failures and how you fixed them.
  - Any additional improvements or refactoring needed.

## **Submission Instructions**
- Ensure your report is **clear and self-contained**, so it can be understood **without running your code**.  
- Upload your final report as a **PDF on Canvas**.