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


**Include in Your Lab Report**  

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
- ✅ **A link to your Pull Request.**  
- ✅ **A copy of your test case.**  
- ✅ **A brief explanation of what your test does and why it is important.**  



## **Task 2 -- Test Driven Development**
You will start by implementing a test case to test creating a counter. Following REST API guidelines, create uses a POST request and returns code ```201_OK``` if successful. Create a counter and then update it.
1. Write the following code in the file ```test_counter.py```. Run ```pytest```. You should see an error ```ModuleNotFoundError```

```python
import pytest

# we need to import the unit under test - counter
from src.counter import app 

# we need to import the file that contains the status codes
from src import status 

```
2. Create a new file in the ```src``` directory called ```counter.py``` and run ```pytest``` again. You should see an ```ImportError```, cannot find ```app``` - ```ImportError: cannot import name 'app' from 'src.counter'```
3. Write the code below and run ```pytest``` again. The tests should run with no error.

```python
from flask import Flask

app = Flask(__name__)
```

The output should be similar to the one below:
```shell
Name              Stmts   Miss  Cover   Missing
-----------------------------------------------
src/__init__.py       0      0   100%
src/counter.py        2      0   100%
src/status.py         6      0   100%
-----------------------------------------------
TOTAL                 8      0   100%
```

1. Let us write our first test case and run ```pytest``` again. 
```python
    def test_create_a_counter():
        """It should create a counter"""
        client = app.test_client()
        result = client.post('/counters/foo')
        self.assert result.status_code == status.HTTP_201_CREATED
```
This time we get <span style="color:red">**RED**</span> - ```AssertionError: 404 !=201```. I didn't find an endpoint called ```/counters```, so I can't possibly post to it." That's the next piece of code we need to go write.
2. Let's go to ```counters.py``` and create that endpoint.  Import status code from the status file - ```from . import status``` and add the code below:

```python
COUNTERS = {}

# We will use the app decorator and create a route called slash counters.
# specify the variable in route <name>
# let Flask know that the only methods that is allowed to called
# on this function is "POST".
@app.route('/counters/<name>', methods=['POST'])
def create_counter(name):
    """Create a counter"""
    app.logger.info(f"Request to create counter: {name}")
    global COUNTERS
    COUNTERS[name] = 0
    return {name: COUNTERS[name]}, status.HTTP_201_CREATED
```

Now we've implemented this first endpoint that should make the test pass. 
When we run ```pytest``` again, we will have <span style="color:green">**GREEN**</span>.

Duplicate names must return a conflict error code.
=====
The second requirement is if the name being created already exists, return a 409 conflict.
Since a lot of the code is going to be repeated, we will <span style="color:blue">**REFACTOR**</span> the repetitive code using the ```fixture``` feature of ```pytest```. 
1. For this example, ```client = app.test_client()``` that is inside ```test_create_a_counter``` test case will be used by more than one test case, let us <span style="color:blue">**REFACTOR**</span> it into new function called ```client``` and decorate it with ```@pytest.fixture()```.
2. Next we will also create a class called ```TestCounterEndPoints``` to group all our counter related tests and move the first test inside the class declaration. 
3. For the last part of our refactoring, we need make the client fixture automatically available to all the test methods within our class. This can be achieved by using the pytest ```usefixtures``` decorator at the class level: ```@pytest.mark.usefixtures("client")```. The finally code is shown below:

```python
@pytest.fixture()
def client():
  return app.test_client()

@pytest.mark.usefixtures("client")
class TestCounterEndPoints:
    """Test cases for Counter-related endpoints"""

    def test_create_a_counter(self, client):
        """It should create a counter"""
        result = client.post('/counters/foo')
        assert result.status_code == status.HTTP_201_CREATED
```

* Now, let us now write the ``test_duplicate_a_counter`` as below. We create a counter called ``bar`` two times. The second time we expect to get a ```HTTP_409_CONFLICT```. 

```python
def test_duplicate_a_counter(self, client):
  """It should return an error for duplicates"""
  result = client.post('/counters/bar')
  assert result.status_code == status.HTTP_201_CREATED
  result = client.post('/counters/bar')
  assert result.status_code == status.HTTP_409_CONFLICT
```
When we run our test cases we obtain
<span style="color:red">**RED**</span> phase - ```AssertionError: 201 != 409```.
It happily created that counter a second time, which is very dangerous because it set it to zero. 
If we update the counter 1, 2, 3, 4, 5, and then we create the same counter again, 
it's going to reset it to zero.

* Let us go <span style="color:blue">**REFACTOR**</span> ```counter.py``` and fix the problem. Before we create any counter, we have to check if it already exists.
Copy and paste the code snippet below and place it right after the code line ```global COUNTERS```.

```python
if name in COUNTERS:
  return {"Message":f"Counter {name} already exists"}, status.HTTP_409_CONFLICT
```
When we run ```pytest``` again we should get the <span style="color:green">**GREEN**</span> phase.

## Your task (15 points)
You will implement the updating the counter by name following the TDD workflow (write test cases and 
write the code to make the test cases pass).
The test cases you will add to are in ```test_counter.py```, and the code you will add is in ```counter.py```. These are the only two files you will work with.
Following REST API guidelines, an update uses a ```PUT``` request and returns code ```200_OK``` if successful. 
Create a counter and then update it. 
You will implement the following requirements:

In ```test_counter.py```, create a test called ```test_update_a_counter(self, client)```. It should implement the following steps:
1. Make a call to Create a counter.
2. Ensure that it returned a successful return code.
3. Check the counter value as a baseline.
4. Make a call to Update the counter that you just created.
5. Ensure that it returned a successful return code.
6. Check that the counter value is one more than the baseline you measured in step 3.

When you run ```pytest```, you should be in the <span style="color:red">**RED**</span> phase.

Next, in ```counter.py```, create a function called ```update_counter(name)```. 
It should implement the following steps:

1. Create a route for method ```PUT``` on endpoint ```/counters/<name>```.
2. Create a function to implement that route.
3. Increment the counter by 1.
4. Return the new counter and a ```200_OK``` return code.

Next, you will write another test case to read a counter. Following REST API guidelines, a read uses a ```GET``` request and returns a ```200_OK``` code if successful. Create a counter and then read it. Here you should figure out the requirements for the test case as well as code you will put in the unit under test.

Push you changes back to the main repository, make a pull request and merge. 

Add to your report of the previous tasks and detail the steps (red/green/refactor phases) you followed to implement the requirements. Include in your report the code snippets you wrote at every step as well as the exceptions you encountered while running ```pytest```. 

**Make your report self-contained so that it is easy to follow without running your code. Remember to add a link to your pull request in the report**
 
Submitting Your Final Report 
======  

The final report should be submitted to **both** the team's repository created in the [Git and GitHub](/teaching/CS472/Timetable/Git_and_GitHub/) Lab and on **Canvas**.  

1. **Prepare your report** – Ensure your final report is saved as:  
   ```<your-names>_TestingLab.pdf```  
2. **Add your report to the repository** – Copy the file and place it in your local forked repository.  
3. **Commit and push** – Commit the changes and push them to your remote forked repository.  
4. **Create a pull request** –  
   - Open a pull request (PR) targeting the **`main` branch** of the Team repository.  
   - Provide a clear and descriptive title and body for the PR.  
5. **Merge the pull request** – A repository maintainer (or yourself, if applicable) should integrate your contribution into the `main` branch.  
6. **Submit on Canvas** – Upload the same report to **Canvas** to complete your submission.  

<!-- This lab aims to evaluate your proficiency in both GitHub usage and software testing. Tasks 2 and 3 will assess both skills, while Tasks 4 and 5 will focus solely on evaluating your software testing abilities. -->

<!-- Importantly, for Tasks 4 and 5, there's no requirement to commit your code to the team repository. The evaluation will be based on your software testing proficiency in the report submitted rather than GitHub usage. However, when submitting your report on Canvas, ensure it includes documentation for all tasks. -->



