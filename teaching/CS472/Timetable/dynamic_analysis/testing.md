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


### **Due Date: Sept 18, 2026**

## **Overview**

In this lab, you will practice the fundamentals of software quality assurance by writing unit tests and analyzing code coverage in Python, and then automate that work with Continuous Integration (CI).

The lab simulates a professional software engineering workflow and is organized into three phases, worth **50 points** in total:

| Phase | Focus | Points |
|-------|-------|--------|
| Phase 1 | **Test Coverage** — analyze existing code and fill testing gaps | 10 |
| Phase 2 | **Test-Driven Development** — build a new API using Red-Green-Refactor | 20 |
| Phase 3 | **Continuous Integration** — automate tests and enforce quality gates with GitHub Actions | 20 |

**You are graded individually, but you work inside your team's repository.** Each student writes their own tests, opens their own pull requests, reviews a teammate's work, and submits their own report. Your team supplies the shared upstream repository and the peer reviewers.

## **Contribution Model**

This lab continues the collaborative workflow introduced in the [Git and GitHub Lab](/teaching/CS472/Timetable/Git_and_GitHub/). The team repository is the authoritative upstream repository, and you work through your individual fork: synchronize with upstream before each contribution, define your work with an issue and acceptance criteria, and submit focused pull requests (PRs) for peer review.

### **Setup PRs (three per team)**

Each phase begins with one setup PR that adds the phase's starter files to the team repository:

| Setup PR | Folder | Also includes |
|----------|--------|---------------|
| Test Coverage setup | `test_coverage_lab` | — |
| TDD setup | `tdd_lab` | The TDD worked example (Phase 2, Step 2) |
| CI setup | `ci_lab` | — |

- Each setup PR is assigned to **one** designated team member. Where possible, assign the three setup PRs to three different members.
- Preparing a setup PR is an additional team responsibility. It does **not** replace that student's own substantive PR.
- A phase's setup PR must be merged before any team member begins their individual contribution for that phase.
- Although only the designated author opens the setup PR, **every student must set up and verify the phase locally** and include that evidence in their report. The setup points assess your own ability to synchronize the repository, install dependencies, and run the project.
- After a setup PR is merged, synchronize your fork before starting your individual work for that phase.

### **Substantive PRs (three per student)**

Each student opens one PR per phase: a test-coverage PR (Phase 1), a TDD PR (Phase 2), and a combined CI PR (Phase 3).

### **Reviews (three per student)**

Each student reviews one teammate's PR in each phase, following a fixed round-robin order that the team agrees on before any PR is opened. Use the same order for setup PRs and substantive PRs.

### **Recommended Progress**

Complete each phase early enough to allow time for review, revision, and merging. Do not wait until the final deadline to begin all three phases. Set internal team deadlines for each setup PR and each round of individual PRs.

## **Workflow Rules for Every Contribution**

These rules apply to all three phases and to both setup and substantive PRs. They are stated once here and are not repeated for each phase.

- **Never push directly to `main`.** Follow the branch protection established in the [Git and GitHub Lab](/teaching/CS472/Timetable/Git_and_GitHub/).
- Every PR must **link to an issue** that states clear acceptance criteria.
- Every PR must be **approved by at least one teammate**, assigned by the team's round-robin order, before merging.
- Reviews must be **concise, technical, and evidence-based** — cite specific tests, coverage output, CI logs, code, or acceptance criteria rather than confirming that the code "looks correct."
- Before merging, the author must address requested changes, resolve all review conversations, resolve merge conflicts, and obtain the required approval.
- Complete your reviews promptly so that teammates are not blocked.

### **Merge Coordination**

Because `main` is protected and several students open PRs that touch shared files, agree on a merge order before individual work begins.

After any PR is merged, every student with an open PR must synchronize their fork with upstream and resolve the resulting conflicts before their own PR can be approved and merged. This matters most in Phases 2 and 3, where students share the same TDD and CI files.

### **Reviewing a Setup PR**

When you review a setup PR, verify that:

- The correct folder and starter files are included.
- A nested `.git/` directory was **not** committed.
- Dependencies can be installed.
- The baseline tests or workflow run successfully.
- For the CI setup PR specifically: `ci.yml` is at `.github/workflows/` in the repository root, not inside `ci_lab/`, and the Actions tab shows a completed run.
- Credentials, generated files, and environment-specific files were not committed.
- The issue's acceptance criteria are satisfied.

## **Software Testing**

Software testing is the process of evaluating and verifying that a software product does what it is supposed to do. Good testing prevents bugs and improves performance ([IBM](https://www.ibm.com/think/topics/software-testing)).

### **Tests: Your Life Insurance!**

Tests are a crucial part of software engineering. They help you:

1. Detect unwanted side effects when modifying code.
2. Gain a deeper understanding of a system's inner workings.

However, the presence of automated tests alone does not guarantee software quality. Ask yourself:

- Do the tests cover the entire system, or are some parts left untested?
- To what extent is each part of the system covered?

**Test coverage** identifies code that has not been exercised, but coverage alone does not establish test quality. Tests must also contain meaningful assertions and verify important behavior.

## **Materials and Tools**

[//]: # (* Session slides [here]&#40;../Testing.pdf&#41;.)

- **Python 3.9 or later.** This exercise was tested with Python `3.9.6` and `3.13.5`. Newer Python 3.9+ versions should also work without major configuration changes. Python 3.8 reached end of life in October 2024 and is no longer supported by the pinned dependencies.
- **An IDE of your choice.** Popular options are [Visual Studio Code](https://code.visualstudio.com/) and [IntelliJ IDEA](https://www.jetbrains.com/idea/).
- **[pytest](https://docs.pytest.org/en/stable/)** — the most popular Python testing framework. It makes it easy to write small, readable tests and scales to complex functional testing.
- **[Flask](https://flask.palletsprojects.com/en/2.3.x/)** — a Python web framework used to build the Counter API in Phase 2.
- *(Optional)* Background reading on [RESTful APIs](https://restfulapi.net/).

Starter repositories, one per phase:

- Phase 1: [Test Coverage](https://github.com/UNLV-CS472-672/test_coverage)
- Phase 2: [Test-Driven Development](https://github.com/UNLV-CS472-672/tdd)
- Phase 3: [Continuous Integration](https://github.com/UNLV-CS472-672/CI)


## **Phase 1: Test Coverage - 10 pts**

In this phase you will practice writing tests and improving test coverage in Python. You will generate and interpret a coverage report to identify untested code, then write tests to cover it.

### **Step 1: Set Up the Test Coverage Lab**

**Every student completes 1.1 through 1.3 locally.** Only the designated setup author completes 1.4 and opens the setup PR, but everyone reports their own setup evidence in 1.5.

#### **1.1 Synchronize Your Fork**

Synchronize your fork with the team's upstream repository and work from your fork. Do not make direct changes to the team's `main` branch.

#### **1.2 Create the Test Coverage Lab Folder**

- Create a folder named `test_coverage_lab` in your working branch to hold all files for this phase. **Use this exact spelling.**
- Copy the [Test Coverage starter files](https://github.com/UNLV-CS472-672/test_coverage) into that folder.
- Do **not** copy the starter repository's `.git/` directory into `test_coverage_lab/`; doing so creates a nested repository.
- Running the suite generates `test.db`, `.coverage`, and `__pycache__/`. These are build artifacts and must not be committed. The starter `.gitignore` already excludes them — copy it across with the other files rather than writing your own.

#### **1.3 Verify the Setup**

Install the required dependencies:

```bash
cd test_coverage_lab
pip install -r requirements.txt
```

Or, for the latest development dependencies:

```bash
pip install -r requirements-dev.txt
```

Run the existing tests with coverage:

```bash
pytest --cov=models --cov-report=term-missing
```

Confirm that the project runs, that the two provided example tests pass, and that a coverage report is generated. Your output should resemble:

```pytest
tests/test_account.py::test_account_role_assignment PASSED               [ 50%]
tests/test_account.py::test_invalid_role_assignment PASSED               [100%]

================================ tests coverage ================================
_______________ coverage: platform darwin, python 3.13.5-final-0 _______________

Name                    Stmts   Miss  Cover   Missing
-----------------------------------------------------
models/__init__.py          7      0   100%
models/account.py          58     26    55%   30, 34, 47-49, 53-56, 60-62, 66-68, 72-76, 80, 84, 94, 98, 102-103
tests/__init__.py           0      0   100%
tests/test_account.py      35      4    89%   27-30
-----------------------------------------------------
TOTAL                     100     30    70%
============================== 2 passed in 0.42s ===============================
```

Your exact numbers will vary with your Python version. The `tests/` rows appear because `pytest.ini` already adds `--cov=models --cov=tests` to every run.

Keep this report. The `Missing` column for `models/account.py` lists the uncovered lines you will target in Step 2.

#### **1.4 Open the Setup PR** *(designated setup author only)*

Create a uniquely named branch, commit the initial setup, and open the **Test Coverage setup PR** against the team repository, linked to a setup issue. This PR must be merged before any student begins their individual test-coverage contribution.

---

### **Step 2: Improve Test Coverage**

#### **2.1 Identify and Claim a Testing Task**

Review the coverage report from Step 1 and identify an uncovered area of `models/account.py`. Create or claim an issue describing the test you will implement, including **clear acceptance criteria**. For example:

> **Issue:** Add a test for insufficient-funds withdrawal
>
> **Acceptance criteria:**
>
> - The test exercises `withdraw()`.
> - The test verifies the behavior when funds are insufficient.
> - The assertions verify the expected result.
> - The test passes locally.
> - The relevant uncovered code is exercised.
> - The PR links to this issue.

Coordinate assignments within your team to avoid duplication. Each student must implement **at least one test case**; in teams of 7–8 students, take one primary item each from the pool below. Claim additional items if you have capacity.

#### **2.2 Test-Coverage Task Pool**

| **Pool Item** | **Description** | **Target Method** |
|---------------|-----------------|-------------------|
| **1** | Test account serialization | `to_dict()` |
| **2** | Test invalid email input | `validate_email()` |
| **3** | Test missing required fields | `validate_required_fields()` |
| **4** | Test positive deposit | `deposit()` |
| **5** | Test deposit with zero/negative values | `deposit()` |
| **6** | Test valid withdrawal | `withdraw()` |
| **7** | Test withdrawal with insufficient funds | `withdraw()` |
| **8** | Test password hashing | `set_password()` / `check_password()` |
| **9** | Test account deactivation/reactivation | `deactivate()` / `reactivate()` |
| **10** | Test email uniqueness enforcement | `validate_unique_email()` |
| **11** | Test deleting an account | `delete()` |

#### **2.3 Create a Branch and Implement Your Test**

After claiming an issue and defining its acceptance criteria:

- Create a uniquely named branch for your contribution.
- Open `tests/test_account.py` and add your test case.
- Include your details in a header comment above the test.
- Keep your changes focused on the issue and use clear, meaningful assertions.
- Run your test and then the full test suite.
- Regenerate the coverage report and confirm the effect of your test.

`tests/test_account.py` already contains two worked example tests. Follow their header-comment convention:

```python
# ===========================
# Test: Account Role Assignment
# Author: John Businge
# Date: 2025-01-30
# Description: Ensure roles can be assigned and checked.
# ===========================

def test_account_role_assignment():
    """Test assigning roles to an account"""
    account = Account(name="John Doe", email="johndoe@example.com", role="user")

    # Assign initial role
    assert account.role == "user"

    # Change role and verify
    account.change_role("admin")
    assert account.role == "admin"
```

The examples cover `change_role()`, which is why it is not in the task pool. Some pool items — `validate_unique_email()` and `delete()`, for instance — do need the database, so use the `db` session and the `setup_account` fixture already defined at the top of the file.

> **Note on pool item 3:** SQLAlchemy does not validate on construction, so `Account()` with no arguments succeeds and raises nothing. The required-field check lives in `validate_required_fields()`, which you call on the constructed object and which raises `DataValidationError`.

Commit in focused commits and push the branch to your fork.

#### **2.4 Open a Pull Request**

Open a PR from your fork to the **team repository**. It must:

- Link to the issue.
- Briefly describe the test and the behavior it verifies.
- Identify the uncovered code it targets.
- Explain how the test satisfies the issue's acceptance criteria.
- Include the relevant test and coverage results.

#### **2.5 Technical Peer Review**

Review your assigned teammate's Phase 1 PR and evaluate:

- **Behavior:** Does the test exercise the intended behavior?
- **Assertions:** Are the assertions specific and meaningful?
- **Coverage:** Does the test cover the intended uncovered code?
- **Regression:** Do the existing tests still pass?
- **Acceptance criteria:** Does the PR satisfy the issue and remain focused?

### **Phase 1 Report Requirements**

- Setup evidence: a screenshot showing the `test_coverage_lab` folder and a successful `pytest` run **on your own machine**, plus links to the team's Test Coverage setup PR and its issue.
- Link to your issue and its acceptance criteria.
- Link to your PR.
- Link to your coverage report or results.
- A brief explanation of the test and the behavior it verifies.
- Link to the teammate's PR you reviewed and to your review comments.
- A short summary of the feedback you received and how you addressed it.
- Link to the approved PR or merge commit.

### **Phase 1 Grading**

- Environment set up correctly (fork synchronized, `test_coverage_lab` folder created, dependencies installed, existing tests passing): **2 points**
- Issue created with clear acceptance criteria for the assigned test case: **1 point**
- Test case correctly implemented with meaningful assertions and evidence that the assigned behavior is exercised: **3 points**
- Pull request linked to the issue, describing the test and including test/coverage evidence: **2 points**
- Technical peer review completed and any feedback received was addressed: **1 point**
- Lab report complete, with all required links and evidence: **1 point**


## **Phase 2: Test-Driven Development (TDD) - 20 pts**

### **The TDD Cycle**

This phase introduces **Test-Driven Development (TDD)** through the following cycle:

1. **<span style="color:red">RED:</span>** Write a test for a missing feature and verify that it fails.
2. **<span style="color:green">GREEN:</span>** Implement the minimum code required to make the test pass.
3. **<span style="color:blue">REFACTOR:</span>** Improve the implementation while keeping the tests passing.

Each student implements one feature of the **Counter API**. See the [**README.md**](https://github.com/UNLV-CS472-672/tdd) in the TDD repository for setup instructions and common errors.

---

### **Step 1: Set Up the TDD Lab**

**Every student completes 1.1 and 1.2 locally.** Only the designated setup author completes 1.3.

#### **1.1 Synchronize and Set Up Your Fork**

- Synchronize your fork with the team's upstream repository.
- Create a folder named `tdd_lab` in your working branch.
- Copy the contents of the [**TDD starter repository**](https://github.com/UNLV-CS472-672/tdd) into `tdd_lab/`.
- Do **not** copy the starter repository's `.git/` directory.

#### **1.2 Install Dependencies and Verify Setup**

```bash
cd tdd_lab
pip install -r requirements.txt
```

Then run:

```bash
pytest --cov=src
```

Because `tests/test_counter.py` contains only a docstring and no tests yet, you should see a coverage table followed by:

```bash
============================ no tests ran in 0.02s =============================
```

pytest exits with **code 5** (`no tests collected`), and coverage prints `CoverageWarning: No data was collected`. Both are expected while the test file is still empty — neither is a setup failure.

If you see errors instead, consult the [**README.md**](https://github.com/UNLV-CS472-672/tdd) for troubleshooting.

#### **1.3 Open the Setup PR** *(designated setup author only)*

Create an issue describing the setup task with clear acceptance criteria. As part of this setup PR, also complete the worked example in Step 2, demonstrating a full <span style="color:red">RED</span>-<span style="color:green">GREEN</span>-<span style="color:blue">REFACTOR</span> cycle.

Then commit your changes, open the **TDD setup PR** against the team repository, and link it to the issue. This PR must be merged before any team member begins their individual TDD contribution.

### **Step 2: Worked Example — RED, GREEN, REFACTOR**

The designated setup author completes and merges this guided example once, as part of the TDD setup PR. **Every other student should read it carefully** before implementing their own feature in Step 3.

Make sure Flask is running as described in the [**README.md**](https://github.com/UNLV-CS472-672/tdd).

#### **2.1 Prepare `src/counter.py`**

The starter repository already contains `src/counter.py` with a bare Flask app. Open it and replace its contents with:

```python
"""
Counter API Implementation
"""
from flask import Flask, jsonify
from . import status

app = Flask(__name__)
```

The app now imports `status`, but the API still provides no counter functionality.

#### **2.2 <span style="color:red">RED</span> — Write a Failing Test**

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

The test fails because the endpoint does not exist. This is the **<span style="color:red">RED</span> phase**.

#### **2.3 <span style="color:green">GREEN</span> — Implement the Minimum Code**

Modify `src/counter.py` to add the missing endpoint:

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

The test now passes. This is the **<span style="color:green">GREEN</span> phase**.

#### **2.4 <span style="color:blue">REFACTOR</span> — Improve the Implementation**

Extract the counter-existence check into a helper function:

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

Run the tests again to verify that the refactoring did not change the behavior. This is the **<span style="color:blue">REFACTOR</span> phase**.

---

### **Step 3: Your TDD Contribution**

Each student is responsible for one test case and its corresponding implementation. In teams of 7–8 students, take one primary feature each from the pool below.

#### **TDD Feature Pool**

| **Pool Item** | **Feature** | **Target API Method** |
|---------------|-------------|-----------------------|
| **1** | Reject invalid (non-alphanumeric) counter names | `POST /counters/<name>` |
| **2** | Retrieve an existing counter | `GET /counters/<name>` |
| **3** | Return 404 for non-existent counter | `GET /counters/<name>` |
| **4** | Increment a counter | `PUT /counters/<name>` |
| **5** | Prevent updating non-existent counter | `PUT /counters/<name>` |
| **6** | Delete a counter | `DELETE /counters/<name>` |
| **7** | Prevent deleting non-existent counter | `DELETE /counters/<name>` |
| **8** | Reset all counters | `POST /counters/reset` |
| **9** | List all counters | `GET /counters` |
| **10** | Handle invalid HTTP methods | Unsupported HTTP methods |

> **Note:** Creating a counter and rejecting duplicates are already implemented by the worked example in Step 2, so they are not in the pool. Every pool item requires code that does not yet exist, so each student can demonstrate a genuine <span style="color:red">RED</span> phase.
>
> **Status codes:** `src/status.py` defines only `HTTP_200_OK`, `HTTP_201_CREATED`, `HTTP_204_NO_CONTENT`, `HTTP_404_NOT_FOUND`, `HTTP_405_METHOD_NOT_ALLOWED`, and `HTTP_409_CONFLICT`. Pool item 1 needs a `400 Bad Request` response, so that student must either add `HTTP_400_BAD_REQUEST = 400` to `src/status.py` as part of their GREEN phase, or use Python's standard `from http import HTTPStatus`. Because `src/status.py` is shared, coordinate that change with your team (see Merge Coordination).

Each student must:

1. Create or claim an issue for their assigned feature.
2. Define clear acceptance criteria.
3. Create a uniquely named branch.
4. Write the test **before** implementing the feature.
5. Demonstrate the **<span style="color:red">RED</span>** phase by showing that the test initially fails.
6. Implement the minimum code required to reach the **<span style="color:green">GREEN</span>** phase.
7. Refactor where useful, or briefly justify why no refactoring was necessary.
8. Run the complete test suite with coverage.
9. Open one focused PR from their fork to the **team repository**, linked to the issue.
10. Participate in technical peer review, address requested changes, resolve conflicts, and merge only after approval.

### **Step 4: Technical Peer Review**

Review your assigned teammate's TDD PR and evaluate:

- **Test:** Does the test verify the behavior described in the issue?
- **RED/GREEN:** Did the test fail first and pass only after the implementation?
- **Refactor:** Does the refactor improve structure without changing behavior?
- **Regression/Coverage:** Do existing tests pass, and does coverage change as expected?
- **Scope/Criteria:** Is the PR focused, and does it satisfy the issue's acceptance criteria?

### **Phase 2 Report Requirements**

- Setup evidence: a screenshot of the `tdd_lab` folder and `pytest` running on your own machine, plus a link to the team's TDD setup PR and its issue.
- Link to your issue and its acceptance criteria.
- Link to your TDD PR and to the test case you wrote.
- A brief explanation of the feature being tested.
- Link to your <span style="color:red">RED</span>/<span style="color:green">GREEN</span>/<span style="color:blue">REFACTOR</span> evidence or test results.
- A short summary of reviewer feedback and how you addressed it.
- Link to the teammate's PR you reviewed and to your review comments.
- A brief statement of the evidence you examined while reviewing (for example: test results, RED/GREEN evidence, coverage report).
- Link to the approved PR or merge commit.

### **Phase 2 Grading**

- Setup and work environment complete (fork synchronized, `tdd_lab` folder created, dependencies installed, setup contribution where assigned): **4 points**
- Issue created with clear acceptance criteria for the assigned feature: **1 point**
- RED phase evidence (failing test written before implementation): **3 points**
- GREEN phase implementation (minimum code required to pass the test): **3 points**
- REFACTOR phase (appropriate improvement made without changing behavior, or a clear justification when no refactoring was needed): **3 points**
- Pull request focused, linked to the issue, and includes RED/GREEN/REFACTOR evidence: **2 points**
- Technical peer review completed and any feedback received was addressed: **2 points**
- Lab report complete, with all required links and evidence: **2 points**


## **Phase 3: Continuous Integration - 20 pts**

This phase builds on the testing and TDD work from the previous phases. You will configure a CI pipeline with **GitHub Actions**, enforce quality gates, and learn to diagnose and fix failing CI runs.

### **Learning Outcomes**

By completing this phase, you will be able to:

- **Set up and extend a GitHub Actions workflow** for CI.
- **Automate test execution** across multiple Python versions.
- **Use caching** to optimize CI runtime.
- **Enforce code coverage thresholds** (fail if coverage is below 80%).
- **Integrate code formatting and linting** (Black and Flake8).
- **Write and run unit tests in CI** and measure coverage before and after changes.
- **Diagnose and fix CI failures** using workflow logs.
- **Create focused PRs** linked to issues and acceptance criteria.
- **Perform technical peer reviews** using tests, coverage, CI results, and acceptance criteria as evidence.

---

### **Step 1: Set Up the CI Lab**

**Every student completes 1.1 through 1.3 locally.** Only the designated setup author completes 1.4.

#### **1.1 Synchronize and Set Up Your Fork**

- Synchronize your fork with the team's upstream repository.
- Create a folder named `ci_lab` in your working branch. **Use the underscore spelling `ci_lab`** — the starter workflow sets `working-directory: ci_lab`, so any other spelling will break the build.
- Copy the starter files from the [**CI starter repository**](https://github.com/UNLV-CS472-672/CI) into `ci_lab/`, with the one exception in 1.2 below.
- Do **not** copy the starter repository's `.git/` directory.
- Running the suite generates `.coverage` and `.pytest_cache/`. These are build artifacts and must not be committed. The starter `.gitignore` already excludes them — copy it across with the other files rather than writing your own.

#### **1.2 Place the Workflow File Correctly**

> **This is the step most teams get wrong.** GitHub Actions only runs workflows found in `.github/workflows/` **at the root of the repository**. A workflow file inside `ci_lab/` is never executed.

The starter repository keeps `ci.yml` at its top level. Move it to the root of your team repository instead of leaving it in the lab folder:

```text
<team-repo-root>/
├── .github/
│   └── workflows/
│       └── ci.yml        <-- the workflow lives here
└── ci_lab/               <-- the application code lives here
    ├── requirements.txt
    ├── pytest.ini
    ├── src/
    └── tests/
```

The workflow already declares `working-directory: ci_lab`, so it will find the code once the file is in the right place.

#### **1.3 Verify the Setup**

Install the dependencies and run the suite locally:

```bash
cd ci_lab
pip install -r requirements.txt
pytest --cov=src --cov-report=term-missing
```

All 22 starter tests should pass at roughly 95% coverage. Then push the branch and confirm on the **Actions** tab that the `CI Workflow` run is triggered and succeeds.

#### **1.4 Open the Setup PR** *(designated setup author only)*

Open the **CI setup PR** against the team repository, linked to a setup issue. This PR must be merged before any student begins their individual CI contribution.

---

### **Step 2: Your Combined CI Contribution**

Each student implements **one distinct CI enhancement**, introduces a controlled failure, diagnoses it from the CI logs, and fixes it — all in a single PR. No two students on a team may select the same enhancement.

1. Select an available enhancement from the list below.
2. Create or claim an issue and define clear acceptance criteria.
3. Synchronize your fork with upstream and create a uniquely named branch.
4. Implement the enhancement.
5. Introduce one controlled failure.
6. Use the CI logs to diagnose the failure and determine its root cause.
7. Implement the fix and re-run CI until it is green.
8. Open one combined CI PR against the team repository.

Your combined CI PR must include:

- A descriptive title.
- A link to the issue and its acceptance criteria.
- Focused changes related to that issue only.
- The workflow/YAML change implementing the enhancement.
- The controlled failure, a CI log excerpt, and your root-cause analysis.
- The fix and evidence of a successful CI rerun.

#### **Available CI Enhancements**

##### **Enhancement 1: Matrix Setup**

- Extend the workflow to run tests on Python 3.9, 3.10, and 3.11.
- Evidence: a CI run showing jobs for all three versions.

##### **Enhancement 2: Dependency Caching**

- Use `actions/cache` to cache Python dependencies.
- Evidence: CI logs showing a cache hit on a subsequent run.

##### **Enhancement 3: Lint and Format Enforcement**

- Add **Flake8** and **Black** checks.
- Note that the starter workflow's existing Flake8 step only selects a few error classes (`E9,F63,F7,F82`), which the starter code passes. A full-strength `flake8 src tests` run reports 57 style violations in the starter code, and `black --check` would reformat three files. Decide whether your enhancement cleans up those pre-existing violations or configures the checks (for example, `--max-line-length`) to a standard your team agrees on, and say which you chose in your PR.
- Evidence: a CI run showing the checks passing, or a failed check followed by a successful fix.

##### **Enhancement 4: Coverage Gate**

- Enforce a minimum coverage threshold of 80% (for example, with `pytest --cov=src --cov-fail-under=80`).
- The starter suite sits at about 95%, so the gate passes initially. Demonstrate that it actually works by making it fail — that can serve as your controlled failure.
- Evidence: a CI run showing the threshold being enforced.

##### **Enhancement 5: Coverage Artifact Upload**

- Configure CI to upload the coverage report as an artifact.
- Evidence: a screenshot or link showing the artifact.

##### **Enhancement 6: CI Visibility and Documentation**

- Add appropriate CI status badges to `README.md`.
- Briefly document the automated checks and explain how contributors can investigate a failed check.
- Evidence: the rendered README, a workflow run, and the documented controlled failure and fix.

##### **Enhancement 7: Split Jobs**

- Separate the workflow into distinct `lint`, `test`, and `coverage` jobs.
- Evidence: a CI run showing the separate jobs.

##### **Enhancement 8: Notifications**

- Add a step that reports CI status on the PR.
- Evidence: the CI status or comment displayed on the PR.

### **Step 3: Technical Peer Review**

Review your assigned teammate's CI PR and evaluate:

- Is the selected enhancement implemented correctly?
- Was a controlled failure clearly demonstrated?
- Do the CI logs support the root-cause analysis?
- Does the fix restore a successful CI run?
- Are the acceptance criteria satisfied without unrelated changes?

In addition to the standard merge requirements, **all required CI checks must pass** before the PR is merged.

### **Phase 3 Report Requirements**

**Repository**

- Link to your fork.
- Evidence that your fork was synchronized with the upstream repository.
- Evidence that the `ci_lab` starter workflow ran successfully for you.

**Combined CI PR**

- Link to your issue and its acceptance criteria.
- Link to your PR.
- Link to the workflow excerpt or a screenshot of it.
- Link to the failing CI log and your root-cause summary.
- Link to the fix commit or PR diff.
- Link to the successful CI run.
- Link to the teammate's PR you reviewed and to your review comments.
- A brief statement of the evidence you examined while reviewing (for example: CI logs, test results, workflow diff).

**Reflection**

Write a short reflection on what you learned about continuous integration, automated testing, coverage and quality gates, CI failure diagnosis, technical peer review, and collaborative software development.

### **Phase 3 Grading**

- Repository setup verified (fork synchronized, `ci_lab` folder created, starter workflow runs successfully): **2 points**
- Issue created with clear acceptance criteria for the selected CI enhancement: **1 point**
- CI enhancement correctly implemented (workflow/YAML change): **4 points**
- Controlled failure introduced and diagnosed using CI logs, with clear root-cause analysis: **3 points**
- Fix implemented and CI rerun to a successful (green) run: **3 points**
- Combined CI PR focused, linked to the issue, and includes all required evidence: **3 points**
- Technical peer review completed and any feedback received was addressed: **2 points**
- Lab report and reflection complete, with all required links and evidence: **2 points**

---

## **Report and Submission**

Submit **one PDF** covering all three phases. Do not submit a separate report for each phase.

Your report must contain the evidence listed under **Phase 1 Report Requirements**, **Phase 2 Report Requirements**, and **Phase 3 Report Requirements**.

Submit the PDF in **both** places:

- **Commit it to your team repository**, and
- **Upload it to Canvas.**

Make your report **clear and self-contained**, using links as the primary evidence trail:

- Include direct links to PRs, issues, CI runs, and review comments for every required deliverable.
- Also paste brief evidence excerpts into the PDF — key coverage table rows, failing and passing CI snippets, and the specific YAML or test fragments you changed — so that graders can understand your work without browsing your fork.

Finally, double-check that your **fork repository link** is correct and public.
