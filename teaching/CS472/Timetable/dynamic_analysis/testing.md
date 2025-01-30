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


### **This individual assignment is due Sept 17th, 2024**

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


Task 1 -- Working with Python Test Coverage
=====
In this task, you will practice writing tests and improving your tests coverage in Python. You will generate a test coverage report and interpret the report to determine which lines of code do not have test cases, and writing test cases to cover those lines.

1. Fork the git project [Python Testing lab](https://github.com/UNLV-CS472-672/test_coverage). Open the IDE, navigate to the directory ```test_coverage``` and create a branch in this format: `testing-<yourFirstname>-<yourLastname>`. Checkout to this branch using this command: ```git checkout -b <your newly created branch bame>```
2. Now, install the required packages by running the command ```pip install pip --upgrade``` followed by ```pip install -r requirements.txt```
3. You will do all your editing work in the file ```tests/test_account.py```.
4. Before writing any code, you should always check that the test cases are passing.Otherwise, when they fail, you won’t know if you broke the code, or if the code was broken before you started.
  * run the ```pytest``` and produce a ```coverage``` report to identify the lines that are missing code coverage:

```pytest
  Name                 Stmts   Miss  Cover   Missing
--------------------------------------------------
models/__init__.py       7      0   100%
models/account.py       40     13    68%   26, 30, 34-35, 45-48, 52-54, 74-75
--------------------------------------------------
TOTAL                   47     13    72%
----------------------------------------------------------------------
Ran 2 tests in 0.349s
```

4. Starting with 72% test coverage. The goal is to reach 100%! Looking at the first missed line, 
line 26 in ```account.py``` to see if we can write a test case for it. To increase the test coverage, we first investigate line 26 in ```models/account.py```. This file is in the ```model``` 
package from the root of the repo. Look at the following code on lines ```25``` and ```26```.

```python
def __repr__(self):
    return '<Account %r>' % self.name
```
Notice that this method is one of the magic methods that is called to represent the class when 
printing it out. We will add a new test case in ```test_account.py``` that calls the ```__repr__()``` method on an Account.

```python
def test_repr():
    """Test the representation of an account"""
    account = Account()
    account.name = "Foo"
    assert str(account) == "<Account 'Foo'>"
```

5. Run ```pytest``` again to ensure line ```26``` is now covered through testing and to determine 
the next line of code for which you should write a new test case:

```angular2html
Name                 Stmts   Miss  Cover   Missing
--------------------------------------------------
models/__init__.py       7      0   100%
models/account.py       40     12    70%   30, 34-35, 45-48, 52-54, 74-75
--------------------------------------------------
TOTAL                   47     12    74%
----------------------------------------------------------------------
Ran 3 tests in 0.387s
```
Note that the overall test coverage has increased from 72% to 74% and the new report does not list line ``26`` in the Missing column. 

6. Next, let us look at the next line of code listed in the lines of code missing tests cases, line 
is ```30```. Examine this line in ```models/account.py``` to find out what that code is doing.

We will look at code of the entire function on lines ```28``` through ```30``` to see what it is doing.
```python
def to_dict(self) -> dict:
    """Serializes the class as a dictionary"""
    return {c.name: getattr(self, c.name) for c in self.__table__.columns}
```
Notice that this code is the ```to_dict()``` method. Now, let us add a new test case in ```test_account.py``` that executes the ```to_dict()``` method on an Account, and thereafter run ```pytest``` again.

```python
def test_to_dict():
    """ Test account to dict """
    rand = randrange(0, len(ACCOUNT_DATA))  # Generate a random index
    data = ACCOUNT_DATA[rand]  # get a random account
    account = Account(**data)
    result = account.to_dict()

    assert account.name == result["name"]
    assert account.email == result["email"]
    assert account.phone_number == result["phone_number"]
    assert account.disabled == result["disabled"]
    assert account.date_joined == result["date_joined"]
```

```angular2html
Name                 Stmts   Miss  Cover   Missing
--------------------------------------------------
models/__init__.py       7      0   100%
models/account.py       40     11    72%   34-35, 45-48, 52-54, 74-75
--------------------------------------------------
TOTAL                   47     11    77%
----------------------------------------------------------------------
Ran 4 tests in 0.368s
```
Note that the overall test coverage increased from 74% to 76%. 

#### Your task - Getting coverage to 100% (20)
In this task to try to get the test coverage to close to 100% as possible. You will examine ```models/account.py``` on lines ```34-35```, ```45-48```, ```52-54```, ```74-75``` to find out what that code is doing.

Using the skills you learn from the [Git and GitHub](/teaching/CS472/Timetable/Git_and_GitHub/) Lab, push you changes back to the main repository and make a pull request. The TA will review and merge your changes accordingly.

**Write a report for Tasks 1. Remember to include the code snippets of your test cases. Make sure that your report is descriptive enough for me to follow without looking at your project code. Additionally, add a link to your pull request in the report**


Task 2 - TDD
=======
Test driven development (TDD) is an approach to software development in which you first write the test cases for the code you wish you had and then write the code to make the test cases pass. In this Task, you will write test cases based on the requirements given to you, and then you will write the code to make the test cases pass.

1. Fork the git project [Test Driven Development](https://github.com/UNLV-CS472-672/tdd). Open the IDE, navigate to the directory ```tdd``` and create a branch in this format: `tdd-<yourFirstname>-<yourLastname>`. Checkout to this branch using this command: ```git checkout -b <your newly created branch bame>```
2. Now, install the required packages by running the command ```pip install pip --upgrade``` followed by ```pip install -r requirements.txt```
3. Open the IDE, navigate to the directory ```tdd```.
      * ```status.py``` -  has some HTTP error codes that we will use when we're checking our error codes
      *  ```pytest.ini``` - In case you have many files in the project, and you are only interested in focusing on a specific directory or file you are testing, so that ```pytest``` only returns testing results for that file, e.g., ```--cov=counter```
      * You will add test cases in ```test_counter.py```. Currently, the file contains only a doc string listing the requirements and no code.
4. You will be working with **HTTP methods** and **REST guidelines** you can take a read [here](https://restfulapi.net/http-methods/)
   
## Creating a counter
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

## Duplicate names must return a conflict error code.
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

Using the skills you learn from the [Git and GitHub](/teaching/CS472/Timetable/Git_and_GitHub/) Lab, push you changes back to the main repository and make a pull request. The TA will review and merge your changes accordingly.

Add to your report of the previous tasks and detail the steps (red/green/refactor phases) you followed to implement the requirements. Include in your report the code snippets you wrote at every step as well as the exceptions you encountered while running ```pytest```. 

**Make your report self-contained so that it is easy to follow without running your code. Remember to add a link to your pull request in the report**
 
Submitting Your Final Report 
=======
The final report will be submitted to the Team's repository created in the [Git and GitHub](/teaching/CS472/Timetable/Git_and_GitHub/) Lab and on **Canvas**.

* Create a branch on your local fork repository called ```python_tests_<yourFirstname>-<yourLastName``` using the following command ```git branch python_tests_<yourFirstname>-<yourLastName```.
* Run the command ```git checkout python_tests_<yourFirstname>-<yourLastName```
* Copy your report--```<your-names>_TestingLab.pdf>``` and paste it in your local fork repository.
* Commit and Push the changes onto your remote fork repository.
* Open a pull request on the ```main branch``` of the Team repository and write an appropriate title and body.
* One of the repository maintainers should integrate your contribution into the main branch.
* You should also submit your report on **Canvas**

<!-- This lab aims to evaluate your proficiency in both GitHub usage and software testing. Tasks 2 and 3 will assess both skills, while Tasks 4 and 5 will focus solely on evaluating your software testing abilities. -->

<!-- Importantly, for Tasks 4 and 5, there's no requirement to commit your code to the team repository. The evaluation will be based on your software testing proficiency in the report submitted rather than GitHub usage. However, when submitting your report on Canvas, ensure it includes documentation for all tasks. -->



