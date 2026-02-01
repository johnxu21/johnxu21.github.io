---
layout: page
title: CS472 - Software Testing & Continuous Integration
permalink: /teaching/CS472/Timetable/dynamic_analysis/
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
    <input type="submit" style="background-color:firebrick;float:left;color:white;width:130px;
height:30px;" value="Testing & CI" />
</form>
<form action="">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="Generative AI" />
</form>
<!-- <form action="/teaching/CS472/Timetable/CI/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="CI" />
</form> -->
<!--form action="/teaching/CS472/Timetable/GPT/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="ChatGPT" />
</form-->
</div>

<br/>
<br/>


### **This individual assignment is due Feb 16th, 2026**


In this lab, you will practice the fundamentals of software quality assurance by writing unit tests and analyzing code coverage using Python. You will also transition to an automated workflow by implementing Continuous Integration (CI) to validate your code automatically. You will continue working with Git and GitHub facilities and submit your final report for this Lab in the **Team's repository** you created and used in the 
[Git and GitHub](/teaching/CS472/Timetable/Git_and_GitHub/) Lab.

Overview
========
This assignment is designed to simulate a professional software engineering workflow. You will progress through three distinct phases:
1. Phase 1 (Test Coverage): Analyzing existing code and filling testing gaps.
2. Phase 2 (Test Drive Development): Building a new API using the Red-Green-Refactor cycle.
3. Phase 3 (Continuous Integration): Automating your tests and enforcing quality gates with GitHub Actions.


Software testing
=========
Software testing is the process of evaluating and verifying that a software product or application does what it’s supposed to do. 
The benefits of good testing include preventing bugs and improving performance [IBM](https://www.ibm.com/think/topics/software-testing?).

### **Tests: Your Life Insurance!**  

Tests are a crucial part of software engineering. They help to:  
1. Detect unwanted side effects when modifying code.  
2. Gain a deeper understanding of a system’s inner workings.  

However, the presence of automated tests alone does not guarantee software quality. Important questions to consider include:  
- Do the tests cover the entire system, or are some parts left untested?  
- To what extent are different parts of the system covered?  

Measuring **test coverage** is a valuable and necessary practice in assessing the effectiveness of a test suite, ensuring that critical components of the software are thoroughly tested.


Materials & Tools Used for this Session
===============

[//]: # (* Session slides [here]&#40;../Testing.pdf&#41;.)
* Install Python `>= 3.8`. This exercise was tested with the following Python versions: `3.8.1, 3.9.5, 3.9.6, 3.9.7` and `3.10.10` but any version of python `3.8+` should work without any major configuration issues.
* Download and install IDE of your choice. Popular options are [Microsoft Visual Studio Code](https://code.visualstudio.com/) and [IntelliJ IDE](https://www.jetbrains.com/idea/)
* [pytest](https://docs.pytest.org/en/stable/) Most popular python testing framework - makes it easy to write small, readable tests, and can scale to support complex functional testing for applications and libraries.
* [flask](https://flask.palletsprojects.com/en/2.3.x/) a web framework, it's a Python module that lets you develop web applications easily.
* (Optional) Read about [RESTFUL API](https://restfulapi.net/)
* [Test Coverage](https://github.com/UNLV-CS472-672/test_coverage) repository.
* [Test Driven Development](https://github.com/UNLV-CS472-672/tdd) repository.
* [Continuous Integration](https://github.com/UNLV-CS472-672/CI) repository.


## **Phase 1: Test Coverage**
In this task, you will practice writing tests and improving your tests coverage in Python. You will generate a test coverage report and interpret the report to determine which lines of code do not have test cases, and writing test cases to cover those lines.

### **Task 1: Set Up Your Team Repository for Test Coverage Lab (5 pts)**

This lab is a continuation of the previous Git and GitHub lab. You will continue working in your existing **team repository**, organizing files using folders rather than creating a new repository.

#### **1. Organize Your Repository**  
- Each team member should create a dedicated folder named `test_coverage_lab` in their **local clone** of the team repository to store all files related to the **Test Coverage Lab**.  
- **Use the exact spelling**: `test_coverage_lab` to maintain consistency and avoid duplicate folders when pushing to the repository.

#### **2. Copy and Set Up the Starter Files**  
- Each team member should **clone the provided Test Coverage repository** and copy the starter files into the `test_coverage_lab/` folder in their **local clone** of the team repository.  
- While copying, ensure that the `.git/` **directory is NOT included** to avoid creating a nested repository.
- No need to push changes to the main repository yet—this step is just for setting up your local environment. 

#### **3. Build and Verify the Setup**  
- Navigate into the `test_coverage_lab` folder.  
- Install the required dependencies from `requirements.txt`:  
  ```bash
  cd test_coverage_lab
  ```
  ```bash
  pip install -r requirements.txt # For stable versions
  ```
  or 
  ```bash
  pip install -r requirements-dev.txt # For latest updates
  ```
- Run `pytest` to check if the provided test cases are passing:
- Ensure that everything compiles successfully before proceeding.
- If any issues arise, debug and resolve them as needed.
- If your tests run successfully, you should see an output similar to this:
  ```pytest
  tests/test_account.py::test_account_role_assignment PASSED                                                                                                                         [100%]
  ---------- coverage: platform darwin, python 3.9.7-final-0 -----------
  Name                 Stmts   Miss  Cover   Missing
  --------------------------------------------------
  models/__init__.py       7      0   100%
  models/account.py       45     18    60%   30, 34, 47-49, 53-55, 59-63, 67, 71, 76, 81-82
  --------------------------------------------------
  TOTAL                   52     18    65%
  ----------------------------------------------------------------------
  1 passed in 1.06s
   ```
- Commit the successful build to your forked repository:
```bash
git add .
git commit -m "Successful setup and initial test run"
git push origin main
```


#### **4. Include in Your Lab Report**  

As the first task in your **final lab report**, include the following:

- Screenshot of Your Terminal  
Provide a screenshot that shows:  
  - The `test_coverage_lab` folder inside your repository.  
  - A successful build of the setup files (i.e., running `pytest` without errors).  
- Commit Link from Your Forked Repository  
Submit a commit link that includes:  
- The `test_coverage_lab` folder added to your repository.  
- Your commit history reflecting the setup process.  

This section serves as proof that you successfully set up the environment before proceeding to Task 1.2.  


### **Task 1.2: Working with Python Test Coverage**


In this task, you will improve test coverage by writing new test cases. All work will be done in the `test_coverage_lab/` folder, and you will submit your changes through a **pull request (PR) from your branch** to the team repository.

#### **1. Understanding the Current Test Coverage**  
- Refer to your previous `pytest` test coverage report from **Task 1**.
- Ensure you understand which lines of code are missing test cases before proceeding.

#### **2. Assigning Test Cases**  
Your team will divide the uncovered code areas among students. Below are suggested tests that need to be implemented.

Each student must implement **at least one test case** for individual assessment.

Teams with **fewer than 11 students** may either:
- Complete all tests (some students implement more than one), **or**
- Implement a subset of tests, as long as **each student completes one**.

Teams should coordinate assignments to avoid duplication.

| **Test Number** | **Description**                          | **Target Method**            |
|---------------|----------------------------------|------------------------------|
| **Student 1**  | Test account serialization         | `to_dict()`                  |
| **Student 2**  | Test invalid email input          | `validate_email()`           |
| **Student 3**  | Test missing required fields      | `Account() initialization`   |
| **Student 4**  | Test positive deposit            | `deposit()`                  |
| **Student 5**  | Test deposit with zero/negative values | `deposit()`              |
| **Student 6**  | Test valid withdrawal            | `withdraw()`                 |
| **Student 7**  | Test withdrawal with insufficient funds | `withdraw()`            |
| **Student 8**  | Test password hashing            | `set_password()` / `check_password()` |
| **Student 9**  | Test account deactivation/reactivation             | `deactivate() / reactivate()`  |
| **Student 10** | Test email uniqueness enforcement     | `validate_unique_email()`    |
| **Student 11** | Test deleting an account        | `delete()`                   |

Your team should discuss who will implement each test. 

#### **3. Writing Your Test Case**
- Open `tests/test_account.py` and add your assigned test case.
- Include your details at the top of your test case:

```python
# ===========================
# Test: Account Role Assignment
# Author: John Businge
# Date: 2026-01-30
# Description: Ensure roles can be assigned and checked.
# ===========================

def test_account_role_assignment():
    """Test assigning roles to an account"""
    account = Account(name="John Businge", email="johnbusinge@example.com", role="user")
    db.session.add(account)
    db.session.commit()

    # Retrieve from database
    retrieved_account = Account.query.filter_by(email="johnbusinge@example.com").first()
    assert retrieved_account.role == "user"

    # Change role and verify
    retrieved_account.change_role("admin")
    db.session.commit()

    updated_account = Account.query.filter_by(email="johnbusinge@example.com").first()
    assert updated_account.role == "admin"
```

#### **4. Committing and Pushing Your Test Case**  

- Create a new branch for your test case:**  
```bash
git checkout -b add-test-<your-test-name>
```
- Commit your changes
- Push to your forked repository
```bash
git push -u origin <your-branch-name>
```

#### **5. Submitting a Pull Request**
- Open a Pull Request (PR) from your branch to the team repository.
- In the PR description, include:
  - brief summary of what your test case does.
  - The line(s) of code covered in `models/account.py`.

#### **6. What to Include in Your Report** 
As a second task in the report, include:  
- **A link to your Pull Request.**  
- **A copy of your test case.**  
- **A brief explanation of what your test does and why it is important.**  



## **Phase 2: Test-Driven Development (TDD) - 15 pts**

### **🔍 Overview**
This phase follows a **Test-Driven Development (TDD)** approach where you will:
1. **Write a test case first** for a missing feature.
2. **Run the test** and observe it **fail** (**Red Phase**).
3. **Implement the feature** to make the test **pass** (**Green Phase**).
4. **Refactor the code** to improve structure (**Refactor Phase**).

Each student will be responsible for **one test case** and the corresponding implementation in the **Counter API**.

Refer to the **[README.md](https://github.com/UNLV-CS472-672/tdd)** file in the TDD repository for **setup instructions** and **common errors & solutions**.

---

### **1. Setting Up Your Work Environment (5 pts)**

#### **1. Organize Your Repository**
- Each team member should **create a new folder** in their local clone of the **team repository**, similar to the previous lab.
- The folder name should be **`tdd_lab`** (use exact spelling for consistency).
- This folder will store all files related to this **TDD Lab**.

#### **2. Copy the Starter Files**
- Copy **all files** from the **root of the provided [tdd repository](https://github.com/UNLV-CS472-672/tdd)** and place them inside your newly created **`tdd_lab/`** folder.
- While copying, ensure that the `.git/` **directory is NOT included** to avoid creating a nested repository.


#### **3. Install Dependencies & Verify Setup**
- Navigate into the **`tdd_lab/`** folder and install the required dependencies:
```bash
  cd tdd_lab
  pip install -r requirements.txt
```

- Run pytest (even though the tests will be empty initially):
```bash
  pytest --cov=src
```
- Expected output (since no tests exist yet):
```bash
  collected 0 items 
```
- If any errors arise, refer to the [README.md](https://github.com/UNLV-CS472-672/tdd) file in the repository for troubleshooting.

#### **4. Commit & Push the Initial Setup**
- After successfully setting up your environment, commit your changes to your forked repository:
```bash
  git add .
  git commit -m "Successful TDD setup and initial test run"
  git push origin main
```

### **Task 2.2. Introduction to TDD (Worked Example)**
- You should read the instructions in the [README.md](https://github.com/UNLV-CS472-672/tdd) to ensure flask is running before they start testing.
- Before you begin writing your own test case, let’s go through a guided example.
- The provided `test_counter.py` file will initially be empty.

#### **Step 1: Create the `src/counter.py` File**
```bash
  touch src/counter.py
```
- Add the following code to `src/counter.py`:

```python
"""
Counter API Implementation
"""
from flask import Flask, jsonify
from . import status

app = Flask(__name__)
```

- Now the `counter.py` file exists, but it does nothing yet.

#### **Step 2: Write a Failing Test**
- Before implementing a new feature, write a test that fails.
- Add the following test case in `tests/test_counter.py`:

```python
import pytest
from src import app
from src import status

@pytest.fixture()
def client():
    """Fixture for Flask test client"""
    return app.test_client()

@pytest.mark.usefixtures("client")
class TestCounterEndpoints:
    """Test cases for Counter API"""

    def test_create_counter(self, client):
        """It should create a counter"""
        result = client.post('/counters/foo')
        assert result.status_code == status.HTTP_201_CREATED
```

- Run `pytest --cov=src`
- Expected failure:

   <span style="color:red">**RED**</span> - `AssertionError: 404 != 201`

- The test fails because the endpoint does not exist yet.

#### **Step 3: Implement the Minimum Code**
- Modify `src/counter.py` to create the missing Flask app. Add the code below:

```python
COUNTERS = {}

@app.route('/counters/<name>', methods=['POST'])
def create_counter(name):
    """Create a counter"""
    if name in COUNTERS:
        return jsonify({"error": f"Counter {name} already exists"}), status.HTTP_409_CONFLICT
    COUNTERS[name] = 0
    return jsonify({name: COUNTERS[name]}), status.HTTP_201_CREATED
```
- Run `pytest --cov=src`

<span style="color:green">**GREEN**</span> - All tests passed ✅

 
#### **Step 4: Refactor for Reusability**
- Refactor the counter creation check into a helper function:
```python
def counter_exists(name):
    """Check if counter exists"""
    return name in COUNTERS
```
- Now update the API to use this function:

```python
@app.route('/counters/<name>', methods=['POST'])
def create_counter(name):
    """Create a counter"""
    if counter_exists(name):
        return jsonify({"error": f"Counter {name} already exists"}), status.HTTP_409_CONFLICT
    COUNTERS[name] = 0
    return jsonify({name: COUNTERS[name]}), status.HTTP_201_CREATED
```

- This makes the code cleaner and reusable.

### **Your tasks**

#### **Task Overview**
Each **student** will be responsible for implementing **one test case** and the corresponding function.

| **Student #** | **Test Case Description** | **Target API Method** |
|--------------|--------------------------|-----------------------|
| **Student 1** | Create a new counter | `POST /counters/<name>` |
| **Student 2** | Prevent duplicate counters | `POST /counters/<name>` |
| **Student 3** | Retrieve an existing counter | `GET /counters/<name>` |
| **Student 4** | Return 404 for non-existent counter | `GET /counters/<name>` |
| **Student 5** | Increment a counter | `PUT /counters/<name>` |
| **Student 6** | Prevent updating non-existent counter | `PUT /counters/<name>` |
| **Student 7** | Delete a counter | `DELETE /counters/<name>` |
| **Student 8** | Prevent deleting non-existent counter | `DELETE /counters/<name>` |
| **Student 9** | Reset all counters | `POST /counters/reset` |
| **Student 10** | List all counters | `GET /counters` |
| **Student 11** | Handle invalid HTTP methods | Unsupported HTTP Methods |

Each student **must:**
1. **Write a test case** inside `tests/test_counter.py`
2. **Implement the feature** inside `src/counter.py`
3. **Run `pytest --cov=src` to verify the test case passes**
4. **Submit a Pull Request (PR) to the team repository**
5. All PRs should be opened on the **main branch** of the team repository.
6. Write a report for the activities.

####  **Step 1: Create a Branch**
```bash
git checkout -b add-test-<your-feature>
git push -u origin <your-branch-name>
```

### **What to Include in Your Report:**
1. **Test Coverage Lab Results**
   - A screenshot or commit link showing your repository setup.
   - A summary of the **test coverage** before and after your test contributions.
   - A description of the test cases you wrote, including the function(s) they cover.
   - A **link to your Pull Request (PR)** for the Test Coverage Lab.

2. **Test-Driven Development Lab Results**
   - A link to your **Pull Request (PR)** for the TDD Lab.
   - A **copy of the test case** you wrote.
   - A **brief explanation** of what your test case does and how it contributes to the Counter API.
   - A **summary of your <span style="color:red;">RED</span>-<span style="color:green;">GREEN</span>-<span style="color:blue;">REFACTOR</span> process**, including:
     - The failing test (**<span style="color:red;">RED</span> Phase**).
     - The implemented feature that made the test pass (**<span style="color:green;">GREEN</span> Phase**).
     - Any code improvements or refactoring you made (**<span style="color:blue;">REFACTOR</span> Phase**).

## **Phase 3: Continuous Integration**
This **Continuous Integration (CI) Lab** builds upon the work done in the **Testing Phase**. In this phase, you will extend the testing process by **enhancing existing test cases** with additional assertions and integrating **GitHub Actions** to automate test execution.  

You will configure a CI pipeline, add tests to improve coverage, enforce code quality gates, and learn to debug failing runs. Unlike earlier labs, this is an **individual assignment**, each student must complete their own contributions, documented and submitted separately.

CI ensures that all code changes are **continuously tested, linted, and validated** before being merged into the repository. You will practice modern DevOps workflows using **Pull Requests (PRs)**, **Issues**, and **peer reviews**.

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

### 2. **One testing PR (required)**
   - Write **at least one new meaningful unit test** (your own authorship) that runs in CI.  
   - Show **coverage before vs. after** and briefly explain what behavior/edge case your test covers.  
   Your testing lab already shows how to run `pytest --cov` and read coverage output.

### 3. **One debugging PR (required)**
   - Introduce a small, controlled failure (failing test, style error, or coverage drop) on a branch.  
   - Use the **Actions logs** to diagnose, then push a fix and re‑run to green (successful run).  
   - In the PR description, paste the failing log snippet and the root‑cause + fix summary.  
   This mirrors the CI failure‑investigation flow in the CI lab steps.

> You may open these PRs **against the team repository** (preferred for collaboration/reviews) **or** work in your **fork** and include links. Either way, grading is **per‑student** via your report.

### Required Sequence (per student)

1. **Sync repo** and confirm the baseline CI workflow runs (Actions tab, green check).  
2. **Write & run your own test** locally and in CI:  
   ```bash
   pytest --cov=src --cov-report=term-missing
   ```

### **What to Include in Your Report:**
1. **Link to your fork repository** (GitHub URL).  
2. **Links to your three PRs** in your fork (Pipeline, Testing, Debugging).  
3. **Coverage evidence**:
   - Before vs. after coverage tables for your Testing PR.  
4. **CI log evidence**:
   - A failing CI log snippet and your fix summary for the Debugging PR.  
5. **Code excerpts**:
   - Your new test function (Testing PR).  
   - YAML snippet showing your workflow change (Pipeline PR).  
6. **A paragraph explaining what you learned about CI and automated quality checks**.  

---

## Submission Instructions

- Your report must include Phase 1 (Test Coverage), Phase 2 (TDD) and Phase 3 (Continuous Integration).
- Do not submit separate reports for each Phase/task. Submit one PDF covering all required details.
- Ensure your report is **clear and self-contained**, so it can be understood **without running your code**.
  - Do not require graders to browse your fork unless for verification.  
  - Paste or screenshot essential evidence (coverage tables, log snippets, YAML/test code) into the PDF.  
- Double-check that your **fork repository link** is correct and public.  









