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


### **This individual assignment is due Sept 20th, 2026**

In this lab, you will practice the fundamentals of software quality assurance by writing unit tests and analyzing code coverage using Python. You will also transition to an automated workflow by implementing Continuous Integration (CI). You will continue the collaborative Git and GitHub workflow introduced in the [Git and GitHub Lab](/teaching/CS472/Timetable/Git_and_GitHub/), where the team repository serves as the authoritative upstream repository. You will work through your individual fork, synchronize it with upstream before beginning each contribution, use issues and acceptance criteria to define your work, and submit focused pull requests for peer review. You will address requested changes before approval and merging, and submit your final report for this lab in the team repository.

Overview
========
This assignment is designed to simulate a professional software engineering workflow. You will progress through three distinct phases:
1. Phase 1 (Test Coverage): Analyzing existing code and filling testing gaps.
2. Phase 2 (Test-Driven Development): Building a new API using the Red-Green-Refactor cycle.
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
* [Test-Driven Development](https://github.com/UNLV-CS472-672/tdd) repository.
* [Continuous Integration](https://github.com/UNLV-CS472-672/CI) repository.


## **Phase 1: Test Coverage**
In this task, you will practice writing tests and improving test coverage in Python. You will generate and interpret a coverage report to identify untested code and write tests to cover it.

### **Task 1: Set Up Your Team Repository for the Test Coverage Lab (5 pts)**
This lab continues the collaborative workflow introduced in the previous [Git and GitHub](/teaching/CS472/Timetable/Git_and_GitHub/) Lab. The **team repository is the authoritative upstream repository**, and you will work through your **individual fork**.

#### **1. Synchronize Your Fork**
Before beginning your work:

- Ensure your fork is synchronized with the team's upstream repository.
- Work from your fork and do not make direct changes to the team's `main` branch.
- Follow the collaborative workflow from the Git and GitHub Lab.

#### **2. Create the Test Coverage Lab Folder**

- Create a folder named `test_coverage_lab` in your working branch to store all files related to this lab.
- **Use the exact spelling:** `test_coverage_lab`.
- Obtain the provided Test Coverage starter files and place them in this folder.
- Ensure the `.git/` directory from the provided repository is **not** copied into `test_coverage_lab/` to avoid creating a nested repository.

#### **3. Verify the Setup**
Navigate into the lab folder and install the required dependencies:

```bash
cd test_coverage_lab
pip install -r requirements.txt
```

or, for the latest development dependencies:

```bash
pip install -r requirements-dev.txt
```

Run the existing tests:

```bash
pytest
```

Ensure that:

- The project builds and runs successfully.
- The provided tests pass.
- The initial coverage report is generated successfully.

You should see output similar to:

```pytest
tests/test_account.py::test_account_role_assignment PASSED [100%]

---------- coverage: platform darwin, python 3.9.7-final-0 -----------
Name                 Stmts   Miss  Cover   Missing
--------------------------------------------------
models/__init__.py       7      0   100%
models/account.py       45     18    60%   30, 34, 47-49, 53-55, 59-63, 67, 71, 76, 81-82
--------------------------------------------------
TOTAL                   52     18    65%
--------------------------------------------------
1 passed in 1.06s
```

Use the coverage report to identify the code that will require additional tests in Task 1.2.

#### **4. Create a Setup Contribution**
Create a uniquely named branch and commit your initial setup using the collaborative workflow from the Git and GitHub Lab.

Open a pull request to the **team repository** and link it to an issue. The setup PR should demonstrate that your environment is working before you begin the testing task.

#### **5. Include in Your Lab Report**
As the first task in your final lab report, include:

- A screenshot showing the `test_coverage_lab` folder and a successful `pytest` run.
- A link to your setup PR.
- A link to the issue associated with the setup.
- Evidence that the initial tests and coverage report were generated successfully.

---

### **Task 2: Working with Python Test Coverage**
In this task, you will improve test coverage by writing new test cases. Your work must follow the collaborative workflow introduced in the Git and GitHub Lab.

#### **1. Identify and Claim a Testing Task**
Review the initial coverage report and identify an uncovered area of `models/account.py`.

Create or claim an issue describing the test you will implement. The issue must include **clear acceptance criteria**.

For example:

**Issue:** Add a test for insufficient-funds withdrawal

**Acceptance criteria:**

- The test exercises `withdraw()`.
- The test verifies the behavior when funds are insufficient.
- The assertions verify the expected result.
- The test passes locally.
- The relevant uncovered code is exercised.
- The PR links to this issue.

Your team should coordinate assignments to avoid duplication.

Each student must implement **at least one test case** for individual assessment.

Teams with fewer than 11 students may either:

- Complete all tests, with some students implementing more than one; or
- Implement a subset of the tests, as long as each student completes at least one.

#### **2. Suggested Test Assignments**

| **Student** | **Description** | **Target Method** |
|-------------|-----------------|-------------------|
| **Student 1** | Test account serialization | `to_dict()` |
| **Student 2** | Test invalid email input | `validate_email()` |
| **Student 3** | Test missing required fields | `Account()` initialization |
| **Student 4** | Test positive deposit | `deposit()` |
| **Student 5** | Test deposit with zero/negative values | `deposit()` |
| **Student 6** | Test valid withdrawal | `withdraw()` |
| **Student 7** | Test withdrawal with insufficient funds | `withdraw()` |
| **Student 8** | Test password hashing | `set_password()` / `check_password()` |
| **Student 9** | Test account deactivation/reactivation | `deactivate()` / `reactivate()` |
| **Student 10** | Test email uniqueness enforcement | `validate_unique_email()` |
| **Student 11** | Test deleting an account | `delete()` |

#### **3. Create a Branch and Implement Your Test**
After claiming an issue and defining its acceptance criteria:

- Create a uniquely named branch for your contribution.
- Open `tests/test_account.py` and add your assigned test case.
- Include your details at the top of your test case.
- Keep your changes focused on the issue.
- Use clear and meaningful assertions.
- Run the relevant tests and the full test suite.
- Generate the coverage report and verify the effect of your test.

For example:

```python
# ===========================
# Test: Account Role Assignment
# Author: John Businge
# Date: 2026-01-30
# Description: Ensure roles can be assigned and checked.
# ===========================

def test_account_role_assignment():
      """Test assigning roles to an account"""
      account = Account(
            name="John Businge",
            email="johnbusinge@example.com",
            role="user"
      )

      db.session.add(account)
      db.session.commit()

      retrieved_account = Account.query.filter_by(
            email="johnbusinge@example.com"
      ).first()

      assert retrieved_account.role == "user"

      retrieved_account.change_role("admin")
      db.session.commit()

      updated_account = Account.query.filter_by(
            email="johnbusinge@example.com"
      ).first()

      assert updated_account.role == "admin"
```

Commit your changes using focused commits and push the branch to your fork.

#### **4. Open a Pull Request**
Open a pull request from your fork to the **team repository**.

The PR must:

- Link to the issue.
- Briefly describe the test and the behavior it verifies.
- Identify the relevant uncovered code.
- Explain how the test satisfies the issue's acceptance criteria.
- Include relevant test and coverage results.

#### **5. Technical Peer Review**
Each student must review at least one teammate's PR.

The review should be **evidence-based and technical**, rather than simply confirming that the code looks correct.

Review the following:

- **Tests:** Does the test exercise the intended behavior?
- **Assertions:** Are the assertions specific and meaningful?
- **Coverage:** Does the test cover the intended uncovered code?
- **Regression:** Do the existing tests continue to pass?
- **Acceptance criteria:** Does the PR satisfy all criteria specified in the issue?
- **Code quality:** Is the test clear, focused, and free of unnecessary duplication?

Provide specific feedback using test results, coverage report, code, or acceptance criteria as evidence.

#### **6. Address Feedback and Merge**
The PR author must:

- Address requested changes.
- Resolve any merge conflicts.
- Respond to review comments.
- Resolve conversations before merging.

The PR may be merged only after receiving the required approval. Once satisfied with the changes, the reviewer should approve the PR and ask the PR author to merge it.

Do not push directly to `main`; changes must be merged through an approved PR.

#### **7. Include in Your Lab Report**
For your individual contribution, include:

- Link to the issue and its acceptance criteria.
- Link to your pull request.
- Copy of your test case.
- Brief explanation of what the test verifies.
- Coverage evidence showing the code addressed by your test.
- Local test results.
- A summary of the technical feedback you received and how you addressed it.
- Link to the teammate's PR that you reviewed.
- Evidence of your technical review and feedback.
- Evidence of approval and merge.



## **Phase 2: Test-Driven Development (TDD) - 15 pts**

### ***🔍 Overview***
This phase introduces **Test-Driven Development (TDD)** through the following cycle:

1. **<span style="color:red">RED:</span>** Write a test for a missing feature and verify that it fails.
2. **<span style="color:green">GREEN:</span>** Implement the minimum code required to make the test pass.
3. **<span style="color:blue">REFACTOR:</span>** Improve the implementation while keeping the tests passing.

Each student will implement one feature for the **Counter API**, following the collaborative Git and GitHub workflow introduced in the previous lab.

Refer to the [**README.md**](https://github.com/UNLV-CS472-672/tdd) in the TDD repository for setup instructions and common errors.

---

### ***1. Setting Up Your Work Environment (5 pts)***
This lab continues the collaborative workflow from the Git and GitHub Lab. The **team repository is the authoritative upstream repository**, and you will work through your **individual fork**.

#### **1.1 Synchronize and Set Up Your Fork**
Before beginning:

- Synchronize your fork with the team's upstream repository.
- Create the `tdd_lab` folder in your working branch.
- Copy the contents of the provided [**TDD repository**](https://github.com/UNLV-CS472-672/tdd) into `tdd_lab/`.
- Do not copy the `.git/` directory from the provided repository.

#### **1.2 Install Dependencies and Verify Setup**
Navigate to the lab folder and install the required dependencies:

```bash
cd tdd_lab
pip install -r requirements.txt
```

Run:

```bash
pytest --cov=src
```

Because no tests exist initially, you should see output similar to:

```bash
collected 0 items
```

If errors occur, refer to the [**README.md**](https://github.com/UNLV-CS472-672/tdd) for troubleshooting.

#### **1.3 Submit the Setup Contribution**
Create an issue describing the setup task and include clear acceptance criteria.

After completing the setup:

- Commit the setup changes to your branch.
- Open a pull request to the **team repository**.
- Link the PR to the issue.
- Address any requested changes before approval.

### ***2. Introduction to TDD (Worked Example)***
Before implementing your assigned feature, complete the following guided example to understand the <span style="color:red">**RED**</span>-<span style="color:green">**GREEN**</span>-<span style="color:blue">**REFACTOR**</span> cycle.

You should also ensure that Flask is running as described in the [**README.md**](https://github.com/UNLV-CS472-672/tdd).

#### **Step 1: Create `src/counter.py`**
Create the file:

```bash
touch src/counter.py
```

Add:

```python
"""
Counter API Implementation
"""
from flask import Flask, jsonify
from . import status

app = Flask(__name__)
```

The file exists, but the API does not yet provide any counter functionality.

#### **Step 2: <span style="color:red">RED</span> — Write a Failing Test**
Before implementing the feature, write a test for the expected behavior in `tests/test_counter.py`:

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

Run:

```bash
pytest --cov=src
```

The test should fail because the endpoint does not exist.

This is the **<span style="color:red">RED</span> phase**.

#### **Step 3: <span style="color:green">GREEN</span> — Implement the Minimum Code**
Modify `src/counter.py` to implement the missing endpoint:

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

Run:

```bash
pytest --cov=src
```

The test should now pass.

This is the **<span style="color:green">GREEN</span> phase**.

#### **Step 4: <span style="color:blue">REFACTOR</span> — Improve the Implementation**
Refactor the counter-existence check into a helper function:

```python
def counter_exists(name):
   """Check if counter exists"""
   return name in COUNTERS
```

Update the endpoint to use it:

```python
@app.route('/counters/<name>', methods=['POST'])
def create_counter(name):
   """Create a counter"""
   if counter_exists(name):
      return jsonify({"error": f"Counter {name} already exists"}), status.HTTP_409_CONFLICT
   COUNTERS[name] = 0
   return jsonify({name: COUNTERS[name]}), status.HTTP_201_CREATED
```

Run the tests again to verify that the refactoring did not change the behavior.

This is the **<span style="color:blue">REFACTOR</span> phase**.

---

### ***3. Your TDD Contribution***
Each student will be responsible for one test case and its corresponding implementation.

| **Student** | **Test Case** | **Target API Method** |
|-------------|---------------|-----------------------|
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

Each student must:

1. Create or claim an issue for their assigned feature.
2. Define clear acceptance criteria for the feature.
3. Create a uniquely named branch.
4. Write the test **before** implementing the feature.
5. Demonstrate the **<span style="color:red">RED</span>** phase by showing the test initially fails.
6. Implement the minimum code required for the **<span style="color:green">GREEN</span>** phase.
7. Refactor the implementation where appropriate.
8. Run the complete test suite and coverage.
9. Open a focused PR from their fork to the **team repository**.
10. Link the PR to the issue.
11. Participate in technical peer review.
12. Address requested changes and resolve conflicts before approval.
13. Merge only after the required approval.

### ***4. Technical Peer Review***
Each student must review at least one teammate's TDD PR.

The review should evaluate:

- **Test correctness:** Does the test verify the behavior described in the issue?
- **Assertions:** Are the assertions specific and meaningful?
- **<span style="color:red">RED</span> phase:** Did the test fail before the feature was implemented?
- **<span style="color:green">GREEN</span> phase:** Does the implementation satisfy the test and acceptance criteria?
- **<span style="color:blue">REFACTOR</span> phase:** Does the refactored code improve structure without changing behavior?
- **Regression:** Do existing tests continue to pass?
- **Coverage:** Does the contribution provide appropriate test coverage?
- **Scope:** Is the PR focused on the assigned issue?
- **Acceptance criteria:** Are all criteria satisfied?

Reviews must provide **evidence-based feedback** using test results, coverage report, code, or acceptance criteria.

### ***5. Address Feedback and Merge***
The PR author must:

- Address reviewer feedback.
- Update the test or implementation where necessary.
- Resolve merge conflicts.
- Resolve review conversations.

The PR may be merged only after receiving the required approval. Once satisfied, the reviewer should approve the PR and ask the PR author to merge.

---

### ***What to Include in Your Report***

#### **Test Coverage Lab**

- Link to your Test Coverage PR.
- Summary of test coverage before and after your contribution.
- Description of the test case you implemented.
- Explanation of the code covered by the test.
- Evidence of your technical peer review.

#### **Test-Driven Development Lab**
For your TDD contribution, include:

- Link to the issue and its acceptance criteria.
- Link to your TDD PR.
- Copy of the test case.
- Brief explanation of the feature being tested.
- Evidence of the **<span style="color:red">RED</span> phase**, showing the test failed before implementation.
- Evidence of the **<span style="color:green">GREEN</span> phase**, showing the test passed after implementation.
- Description of any **<span style="color:blue">REFACTOR</span>** changes.
- Final test and coverage results.
- Summary of reviewer feedback and how you addressed it.
- Link to the teammate's PR you reviewed.
- Evidence of your technical review and feedback.
- Evidence of approval and merge.

## **Phase 3: Continuous Integration**
This **Continuous Integration (CI) Lab** builds upon the testing and TDD work completed in the previous phases. You will extend the testing process by enhancing existing tests and integrating **GitHub Actions** to automate testing and code-quality checks.

You will configure a CI pipeline, improve test coverage, enforce quality gates, and learn to diagnose and fix failing CI runs. All contributions will follow the collaborative Git and GitHub workflow introduced in the Git and GitHub Lab.

The **team repository is the authoritative upstream repository**. You will work through your individual fork, synchronize with upstream before each contribution, define work through Issues and acceptance criteria, and submit focused PRs to the team repository for technical peer review.

## Learning Outcomes
By completing this lab, you will be able to:

- **Set up and extend a GitHub Actions workflow** for CI.
- **Automate test execution** across multiple Python versions.
- **Use caching** to optimize CI runtime.
- **Enforce code coverage thresholds** (fail if coverage < 80%).
- **Integrate code formatting and linting** (Black + Flake8).
- **Write and run unit tests in CI** and measure coverage before and after changes.
- **Diagnose and fix CI failures** using workflow logs.
- **Create focused PRs** linked to Issues and acceptance criteria.
- **Perform technical peer reviews** using tests, coverage, CI results, and acceptance criteria as evidence.

---

## Repository Setup
Before beginning your individual contributions:

1. Synchronize your fork with the team's upstream repository.
2. Create a folder named `ci_lab` in your working branch.
3. Download the starter files from the [CI Lab repository](https://github.com/UNLV-CS472-672/CI).
4. Place the starter files in the `ci_lab` folder.
5. Ensure `.gitignore` excludes unnecessary files such as `.pyc`, `__pycache__/`, and environment-specific files.
6. Verify that the starter project and existing CI workflow run successfully.
7. Submit the setup as a focused contribution following the collaborative workflow from the Git and GitHub Lab.

---

## General PR Requirements
You will complete **three contributions** during this lab:

1. **Pipeline PR**
2. **Testing PR**
3. **Debugging PR**

Each PR must:

- Have a descriptive title.
- Link to its Issue.
- Include clear acceptance criteria.
- Contain focused changes related to the Issue.
- Include relevant test and CI evidence.
- Address reviewer feedback before merging.
- Pass all required CI checks.
- Be approved before merging.

---

## Individual Tasks - Three PRs per Student
Each student must complete **three separate contributions**, each associated with an Issue and submitted as a PR to the team repository.

### **1. Pipeline PR - One Unique CI Enhancement**
Each student must implement **one distinct pipeline enhancement** from the list below. No two students in the same team should select the same enhancement.

Before starting:

1. Select an available enhancement.
2. Create or claim an Issue.
3. Define clear acceptance criteria.
4. Synchronize your fork with upstream.
5. Create a uniquely named branch.
6. Implement the enhancement.
7. Test the workflow locally where applicable.
8. Open a PR to the team repository.

Your Pipeline PR must include:

- The YAML change implementing the enhancement.
- At least one meaningful test authored by you.
- Evidence that the existing test suite runs successfully.
- A short explanation of how the enhancement improves CI.
- CI evidence demonstrating that the enhancement works.

### **Available Enhancements**

#### **1. Matrix Setup**
- Extend the workflow to run tests on Python 3.9, 3.10, and 3.11.
- Evidence: CI run showing jobs for all three versions.

#### **2. Dependency Caching**
- Use `actions/cache` to cache Python dependencies.
- Evidence: CI logs showing a cache hit on a subsequent run.

#### **3. Lint and Format Enforcement**
- Add **Flake8** and **Black** checks.
- Evidence: CI run showing the checks passing, or a failed check followed by a successful fix.

#### **4. Coverage Gate**
- Enforce a minimum coverage threshold of 80%.
- Evidence: CI run showing the coverage threshold being enforced.

#### **5. Coverage Artifact Upload**
- Configure CI to upload the coverage report as an artifact.
- Evidence: Screenshot or link showing the artifact.
#### **6. Status Badges in README**
- Add build, lint, and/or coverage badges to `README.md`.
- Evidence: Updated README rendered on GitHub.

#### **7. Split Jobs**
- Separate the workflow into distinct `lint`, `test`, and `coverage` jobs.
- Evidence: CI run showing the separate jobs.

#### **8. Notifications**
- Add a step that reports CI status on the PR.
- Evidence: CI status/comment displayed on the PR.

> **Note:** If another student has already completed an enhancement, select a different enhancement. Each student must make an independent contribution and provide their own implementation and evidence.

---


### **2. Testing PR - Add a Meaningful Test**
For your second contribution:

1. Create or claim an Issue describing the behavior or edge case to be tested.
2. Define clear acceptance criteria.
3. Synchronize your fork with upstream.
4. Create a uniquely named branch.
5. Add at least one meaningful unit test.
6. Run the test locally and through CI.
7. Measure coverage before and after the change.
8. Open a focused PR to the team repository.
9. Participate in technical peer review.

The test should verify meaningful behavior rather than simply increase the coverage percentage.

Run:

```bash
pytest --cov=src --cov-report=term-missing
```

Your PR should include:

- The new test.
- The behavior or edge case being tested.
- Coverage before and after.
- Test results.
- CI results.
- Explanation of how the test satisfies the Issue's acceptance criteria.

---

### **3. Debugging PR - Diagnose and Fix a CI Failure**
For your third contribution:

1. Create or claim an Issue describing the CI failure scenario.
2. Define acceptance criteria for diagnosing and resolving the failure.
3. Synchronize your fork with upstream.
4. Create a uniquely named branch.
5. Introduce a small, controlled failure such as a failing test, a style violation, or a coverage failure.
6. Push the change and allow CI to fail.
7. Use the GitHub Actions logs to identify the cause.
8. Implement the fix.
9. Re-run CI and verify that it passes.
10. Open a PR to the team repository.
11. Participate in technical peer review.

The PR description must include:

- The failing CI log or relevant excerpt.
- The identified root cause.
- The change made to fix the problem.
- Evidence of the successful CI run.
- An explanation of how the acceptance criteria were satisfied.

---

## Technical Peer Review
Each student must review at least one teammate's CI PR.

The review should be **technical and evidence-based**.

Reviewers should evaluate:

### **Pipeline PR**

- Is the workflow configuration correct?
- Does the new CI feature actually execute?
- Does it enforce the intended quality check?
- Do the CI jobs produce the expected results?
- Does the change satisfy the Issue's acceptance criteria?
- Does it introduce unnecessary complexity?

### **Testing PR**

- Does the test verify meaningful behavior?
- Are the assertions appropriate?
- Does the test cover the intended edge case?
- Does coverage change as expected?
- Do existing tests continue to pass?
- Does the test pass in CI?
- Are the acceptance criteria satisfied?

### **Debugging PR**

- Was the failure reproduced successfully?
- Does the CI log support the identified root cause?
- Does the proposed fix address the actual cause?
- Does the fix restore a successful CI run?
- Were unrelated changes avoided?
- Are the acceptance criteria satisfied?

---

## Address Feedback and Merge
The PR author must:
- Address requested changes.
- Respond to reviewer comments.
- Resolve merge conflicts.
- Ensure all required CI checks pass.
- Resolve review conversations.

A PR may be merged only after receiving the required approval.

Once satisfied with the changes, the reviewer should approve the PR and ask the PR author to merge.

---

## Required Evidence and Report
Your final report should include:

### **1. Repository**

- Link to your fork.
- Evidence that your fork was synchronized with the upstream repository.

### **2. Pipeline PR**

- Issue link and acceptance criteria.
- PR link.
- YAML excerpt showing your CI enhancement.
- Explanation of the enhancement.
- CI evidence demonstrating that it works.
- Technical review evidence.

### **3. Testing PR**

- Issue link and acceptance criteria.
- PR link.
- Your new test function.
- Description of the behavior or edge case tested.
- Coverage before and after.
- Test and CI results.
- Technical review evidence.

### **4. Debugging PR**

- Issue link and acceptance criteria.
- PR link.
- Failing CI log excerpt.
- Root-cause analysis.
- Description of the fix.
- Successful CI result after the fix.
- Technical review evidence.

### **5. Reflection**
Write a short reflection explaining what you learned about:

- Continuous Integration.
- Automated testing.
- Coverage and quality gates.
- CI failure diagnosis.
- Technical peer review.
- Collaborative software development.

---

## Submission Instructions

- Your report must include Phase 1 (Test Coverage), Phase 2 (TDD) and Phase 3 (Continuous Integration).
- Do not submit separate reports for each Phase/task. Submit one PDF covering all required details.
- Ensure your report is **clear and self-contained**, so it can be understood **without running your code**.
  - Do not require graders to browse your fork unless for verification.  
  - Paste or screenshot essential evidence (coverage tables, log snippets, YAML/test code) into the PDF.  
- Double-check that your **fork repository link** is correct and public.  









