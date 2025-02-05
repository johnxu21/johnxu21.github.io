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
4. ✅ If successful, you should see a **green checkmark** indicating the workflow has run successfully.
5. ❌ **If you see an error (red ❌ or failure message):**
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
1. Go to your **GitHub repository**.
2. Click on the **"Actions"** tab and select the latest workflow run.
3. ✅ **If successful, you should see output similar to:**

```diff
==================== test session starts ====================
collected X items
... (list of passing tests)
================== coverage report ===================
```
4.  ❌ **If Errors Occur:**
- Click on the **failed workflow run** in the **"Actions"** tab.
- Check the **error logs** to identify the issue.
- Ensure all dependencies are correctly installed in `requirements.txt`.
- Fix any **failing tests** and push the changes:
   ```bash
   git add .
   git commit -m "Fixed failing tests"
   git push origin main

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
  - 🔴 **Syntax errors** (`E9`)
  - ⚠️ **Undefined names** (`F63`, `F7`, `F82`)
  - 📝 **General code style issues**

---

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
3. ✅ **If successful**, the workflow will complete without issues.
4. ❌ **If errors occur**, Flake8 will list the violations. Fix them and push the changes.

```bash
# Example: Fix Flake8 issues, then commit and push
git add .
git commit -m "Fixed Flake8 linting errors"
git push origin main
```

# **Writing & Automating Your Test Case in CI**

Now that you have successfully configured **Continuous Integration (CI) with GitHub Actions**, your next task is to **extend test coverage** by adding new test cases that will be automatically executed in CI.

---

# **Extending Tests and Automating CI**

## **Task Overview**
In this step, you will **extend test coverage** by implementing new test cases that build upon the work done in the Testing Lab. Your goal is to **write and automate these new tests** in GitHub Actions, ensuring they run successfully as part of the CI pipeline.

**Important:**  
- You **do not** need to modify the `counter.py` API implementation unless you are performing **necessary refactorings** to make your tests pass.
- The API is largely complete from the Testing Lab. Focus on **adding new test cases** and ensuring they are properly automated in CI.

---

## **Test Case Assignments**
Each student will extend the Counter API by implementing and testing new features beyond the basics covered in the Testing Lab.

| **Student #** | **New Test Case Description** | **Target API Method** |
|--------------|------------------------------|-----------------------|
| **Student 1** | Get total count of all counters | `GET /counters/total` |
| **Student 2** | Retrieve the top N highest counters | `GET /counters/top/<n>` |
| **Student 3** | Retrieve the top N lowest counters | `GET /counters/bottom/<n>` |
| **Student 4** | Set a counter to a specific value | `PUT /counters/<name>/set/<value>` |
| **Student 5** | Ensure setting a counter to a negative value is not allowed | `PUT /counters/<name>/set/<value>` |
| **Student 6** | Reset a single counter | `POST /counters/<name>/reset` |
| **Student 7** | Return an error when resetting a non-existent counter | `POST /counters/<name>/reset` |
| **Student 8** | Return a count of how many counters exist | `GET /counters/count` |
| **Student 9** | Retrieve counters with values greater than a given threshold | `GET /counters/greater/<threshold>` |
| **Student 10** | Retrieve counters with values less than a given threshold | `GET /counters/less/<threshold>` |
| **Student 11** | Validate counter names (e.g., prevent special characters) | `POST /counters/<name>` |

---

## **🛠 Steps to Implement Your Test Case**

### **1. Assign Test Cases**
- Coordinate with your team to ensure each student implements a **different test case** from the list above.

---

### **2. Write the Test Case**
- Open `tests/test_counter.py` and add your assigned test case.
- Follow the same structure you used in the **Testing Lab**, ensuring:
  - **Proper function documentation**
  - **Use of pytest fixtures for the test client**
  - **Assertions for both status codes and response content**

**Example Test Case Format**
```python
# ===========================
# Test: Retrieve total count of all counters
# Author: Jane Doe
# Date: 2025-02-05
# Description: Ensures the API returns the correct total count of all counters.
# ===========================

def test_get_total_counters(client):
    """Test retrieving the total count of all counters"""
    client.post("/counters/test1")  # Create a test counter
    client.post("/counters/test2")  # Create another counter
    response = client.get("/counters/total")  # Fetch total count
    
    # Assertions: Validate response
    assert response.status_code == 200
    assert response.get_json() == {"total": 2}
```

### **3. Commit and Push Your Changes**
Once you have added your test case, create a new branch and follow your regular Git workflow to commit and push the changes to your **forked** team repository.

- **Create a new branch** following your team’s naming conventions (e.g., `add-test-total-counters`).
- **Commit your test case** to `tests/test_counter.py`.
- **Push your changes** to your forked repository.

Once pushed, you are ready to submit a **Pull Request (PR)**.

### **4. Submit a Pull Request**

### **5. Verify CI Automation**