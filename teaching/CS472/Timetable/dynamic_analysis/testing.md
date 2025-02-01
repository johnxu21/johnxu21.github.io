---
layout: page
title: CS472 - Software Testing
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
height:30px;" value="Testing" />
</form>
<form action="/teaching/CS472/Timetable/CI/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="CI" />
</form>
<form action="/teaching/CS472/Timetable/GPT/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="CHAT GPT" />
</form>
</div>

<br/>
<br/>


### **This individual assignment is due Feb 5th, 2025**

In this Lab your will practice writing unit tests and analysing test coverage using Python programming language.
In the Lab you will also continue working with Git and GitHub facilities. You will submit your final report for this Lab in the **Team's repository** you created and used in the 
[Git and GitHub](/teaching/CS472/Timetable/Git_and_GitHub/) Lab.


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


Task 1 -- Test Coverage
===
In this task, you will practice writing tests and improving your tests coverage in Python. You will generate a test coverage report and interpret the report to determine which lines of code do not have test cases, and writing test cases to cover those lines.

### **Task 1: Set Up Your Team Repository for Test Coverage Lab (5 pts)**

This lab is a continuation of the previous Git and GitHub lab. You will continue working in your existing **team repository**, organizing files using folders rather than creating a new repository.

#### **1. Organize Your Repository**  
- Each team member should create a dedicated folder named `test_coverage_lab` in their **local clone** of the team repository to store all files related to the **Test Coverage Lab**.  
- **Use the exact spelling**: `test_coverage_lab` to maintain consistency and avoid duplicate folders when pushing to the repository.

#### **2. Copy and Set Up the Starter Files**  
- Each team member should **clone the provided Test Coverage repository** and copy the starter files into the `test_coverage_lab/` folder in their **local clone** of the team repository.  
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
- ```bash
  pip install -r requirements-dev.txt # For latest updates
  ```
- 
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

1. Screenshot of Your Terminal**  
Provide a screenshot that shows:  
- The `test_coverage_lab` folder inside your repository.  
- A successful build of the setup files (i.e., running `pytest` without errors).  

2. Commit Link from Your Forked Repository**  
Submit a commit link that includes:  
- The `test_coverage_lab` folder added to your repository.  
- Your commit history reflecting the setup process.  

This section serves as proof that you successfully set up the environment before proceeding to Task 1.2.  


# **Task 1.2: Working with Python Test Coverage**


In this task, you will improve test coverage by writing new test cases. All work will be done in the `test_coverage_lab/` folder, and you will submit your changes through a **pull request (PR) from your branch** to the team repository.

### **1. Understanding the Current Test Coverage**  
- Refer to your previous `pytest` test coverage report from **Task 1**.
- Ensure you understand which lines of code are missing test cases before proceeding.

### 2. Assigning Test Cases  
Your team will divide the uncovered code areas among students. Below are suggested tests that need to be implemented:  

| **Test Number** | **Description**                          | **Target Method**             |
|---------------|----------------------------------|------------------------------|
| **Student 1**  | Test account serialization         | `to_dict()`                   |
| **Student 2**  | Test invalid email input          | `validate_email()`            |
| **Student 3**  | Test missing required fields      | `Account() initialization`    |
| **Student 4**  | Test positive deposit            | `deposit()`                   |
| **Student 5**  | Test deposit with zero/negative values | `deposit()`              |
| **Student 6**  | Test valid withdrawal            | `withdraw()`                  |
| **Student 7**  | Test withdrawal with insufficient funds | `withdraw()`            |
| **Student 8**  | Test password hashing            | `set_password()` / `check_password()` |
| **Student 9**  | Test role assignment             | `change_role()`               |
| **Student 10** | Test invalid role assignment     | `change_role()`               |
| **Student 11** | Test deleting an account        | `delete()`                    |

Your team should discuss who will implement each test.

### 3. Writing Your Test Case
- Open `tests/test_account.py` and add your assigned test case.
- Include your details at the top of your test case:

```python
# ===========================
# Test: Account Role Assignment
# Author: John Businge
# Date: 2025-01-30
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

### 4. Committing and Pushing Your Test Case  

- Create a new branch for your test case:**  
```bash
git checkout -b add-test-<your-test-name>
```
- Commit your changes
- Push to your forked repository

### 5. Submitting a Pull Request
- Open a Pull Request (PR) from your branch to the team repository.
- In the PR description, include:
  - brief summary of what your test case does.
  - The line(s) of code covered in `models/account.py`.

### 6. Lab Report Submission  

As a second task in the report, include:  
- **A link to your Pull Request.**  
- **A copy of your test case.**  
- **A brief explanation of what your test does and why it is important.**  



# **📌 Task 2: Test-Driven Development (TDD) Lab Assignment (15 pts)**

## **🔍 Overview**
This lab follows a **Test-Driven Development (TDD)** approach where you will:
1. **Write a test case first** for a missing feature.
2. **Run the test** and observe it **fail** (**Red Phase**).
3. **Implement the feature** to make the test **pass** (**Green Phase**).
4. **Refactor the code** to improve structure (**Refactor Phase**).

Each student will be responsible for **one test case** and the corresponding implementation in the **Counter API**.

Refer to the **[README.md](https://github.com/UNLV-CS472-672/tdd)** file in the TDD repository for **setup instructions** and **common errors & solutions**.

---

## **1. Setting Up Your Work Environment (5 pts)**

### **1. Organize Your Repository**
- Each team member should **create a new folder** in their local clone of the **team repository**, similar to the previous lab.
- The folder name should be **`tdd_lab`** (use exact spelling for consistency).
- This folder will store all files related to this **TDD Lab**.

### **2. Copy the Starter Files**
- Copy **all files** from the **root of the provided [tdd repository](https://github.com/UNLV-CS472-672/tdd)** and place them inside your newly created **`tdd_lab/`** folder.

### **3. Install Dependencies & Verify Setup**
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

### **4. Commit & Push the Initial Setup**
- After successfully setting up your environment, commit your changes to your forked repository:
```bash
  git add .
  git commit -m "Successful TDD setup and initial test run"
  git push origin main
```

## **Task 2.2. Introduction to TDD (Worked Example)**
- You should read the instructions in the [README.md](https://github.com/UNLV-CS472-672/tdd) to ensure flask is running before they start testing.
- Before you begin writing your own test case, let’s go through a guided example.
- The provided `test_counter.py` file will initially be empty.

### **Step 1: Create the `src/counter.py` File**
```bash
  touch src/counter.py
```
- Add the following code to `src/counter.py`:

```python
    """
    Counter API Implementation
    """
    from flask import Flask

    app = Flask(__name__)
```

- Now the `counter.py` file exists, but it does nothing yet.

### **Step 2: Write a Failing Test**
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

### **Step 3: Implement the Minimum Code**
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

 
### **Step 4: Refactor for Reusability**
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

## **Your tasks**

### **Task Overview**
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
5. All PRs should be opened on the main branch of the team repository

###  **Step 1: Create a Branch**
```bash
git checkout -b add-test-<your-feature>
```

## **Final Report Submission (10 pts)**

After completing all tasks in the lab, compile a **single report** documenting your work. This report should be **comprehensive** and should include **all tasks**, including **Test Coverage** and **Test-Driven Development (TDD)**.

### ✅ **What to Include in Your Report:**
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

### 📤 **Submission Instructions**
- Upload your final report as a **PDF** on Canvas.
- Ensure your report is **clear and self-contained**, so it can be understood **without running your code**.



