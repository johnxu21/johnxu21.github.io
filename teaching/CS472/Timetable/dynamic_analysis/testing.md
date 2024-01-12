---
layout: page
title: CS472 - Dynamic Analysis
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


### **This individual assignment is due September 26th, 2023**

In this Lab your will practice writing unit tests and analysing test coverage using two programming languages: Java and Python.
In the Lab you will also continue working with Git and GitHub facilities. You will make all your contributions
for this Lab in the **Team's repository** you created and used in the 
[Git and GitHub](/teaching/CS472/Timetable/Git_and_GitHub/) Lab.


Dynamic Analysis
=========

Dynamic analysis is “the analysis of the properties of a running software system” 
[[Ball1999](https://ansymore.uantwerpen.be/system/files/Ball1999.pdf)]. 
It is complementary to static analysis techniques. Some properties that cannot be 
studied through static analysis can be examined with dynamic analysis and vice versa. 
The applications of dynamic analysis techniques are very broad: program comprehension, 
system verification, resource profiling, test analysis, etc. In this session, we focus on 
one very important aspect of dynamic analysis: **Testing**.

"Tests: Your Life Insurance!" 
Tests are essential for software engineering activities. They can help you: 
1. to reveal unwanted side effects of changing the code 
2. to understand the inner workings of a system.

The presence of automated tests does however not offer any guarantee about its quality. 
Do the tests cover the whole system or are some parts left untested? 
Which parts are covered to which extent? Hence, measuring test coverage is a useful, even 
necessary, way to assess the quality and usefulness of a test suite in the context of software engineering.

Materials & Tools Used for this Session
===============

[//]: # (* Session slides [here]&#40;../Testing.pdf&#41;.)
* [IntelliJ IDE](https://www.jetbrains.com/idea/) (you can use [Eclipse](https://www.eclipse.org/) at your discretion, but it may require some adaptations for the project we are using during the lab sessions)
* [JPacman](https://github.com/johnxu21/jpacman) repository.
* [JaCoCo](https://www.jacoco.org/jacoco/index.html) is an eclipse plugin for coverage analysis. It is also available as a maven repository. Newer versions of IntelliJ already have this plugin pre-installed as a part of the test coverage plugin.
* [nosetests](https://nose.readthedocs.io/en/latest/) extends python unittest to make testing easier.
* [flask](https://flask.palletsprojects.com/en/2.3.x/) a web framework, it's a Python module that lets you develop web applications easily.


Setup / Preparation
=============

[//]: # (First, make sure to fork the JPacman from the [Prof's repository]&#40;https://github.com/johnxu21/jpacman&#41; into your GitHub account. It is necessary to fork the project because the free version of CodeScene can only see projects from your own account.)

To start getting acquainted with the JPacman source code. Download/Clone the JPacman project from the 
[Prof's repository](https://github.com/johnxu21/jpacman) and open it on IntelliJ; build it. JPacman uses Gradle as a built/dependency manager. 
Make sure you can build and run it before doing any source code modification.
Now look at the source code and try to understand its internal structure. In the "docs/uml" folder there are two simplified UML diagrams.

Task 1 -- JPacman Test Coverage
===========
 
We will begin by using the [IntelliJ IDE](https://www.jetbrains.com/idea/) test coverage plugin. 
The testing and coverage plugins should be enabled by default. If you are not sure, check under ```IntelliJ IDEA > Preferences > Plugins > installed``` if your 
plugins called ```Code Coverage for Java```, ```JUnit```, and ```TestNG``` are enabled.
 
First, make sure that you can test your JPacman, by using the following command line in the 
[IntelliJ IDE](https://www.jetbrains.com/idea/) terminal:
```
./gradlew test
```
**Note:** Remember to set the project to point to the JDK version on which it was built. Look at ```External Libraries``` under the 
Project's folder in IntelliJ IDE to see the JDK version.

Now, right-click on the ```test``` folder (inside the ```src``` folder) and select the option "Run 'Tests' 
in ```jpacman.test``` with Coverage". If that option is not available, select "Build Module 
```jpacman.test```" and after the build right-click again and the option  "Run 'Tests' in 
```jpacman.test``` with Coverage" should be available.

Alternatively, you can also right-click on the Gradle task ```test```, inside the module ```Task->verification```
shown in the ```Gradle plugin``` (default position is a collapsed tab on the right part of your IntelliJ). 
Select ```Run 'jpacman [test]' with Coverage```. This Gradle task should produce the same coverage. 
Therefore, use whichever you prefer. 
 
If everything executed without errors, you should see a new window showing the code coverage. 
Please try to remember this coverage (or take a screenshot to not depend on your memory).
 
**Question:**
* Is the coverage good enough?

Task 2 -- Increasing Coverage on JPacman 
===================
  
For the second task, we will increase the coverage on JPacman. Doing that is very simple, 
we just need to write more tests. In this task, we are going to write one new test case. 
As you have seen from **Task 1** that the coverage for several packages is zero percent.
 
Let's create a simple ```unit test``` on a method. We will test the ```isAlive()``` method in class ```Player``` 
(package ```level```). You should look at the ```DirectionTest``` class (folder ```test```, package ```board```) as a template 
for your test case. **The hardest part is instantiating a ```Player``` object as it requires other objects.** 
The ```PlayerFactory``` class is responsible for creating instances of ```Player```. And, ```PlayerFactory``` 
constructor requires a ```PacManSprites``` (package ```sprites```) object. Therefore, you need to instantiate a 
```PacManSprites``` object, to pass it on to the constructor of ```PlayerFactory```, and only then you can 
call the factory method to create a ```Player```.
 
Create the package ```level``` in the ```test``` folder. Then, create the class ```PlayerTest``` inside this 
package ```level```. Now you can write the test case for testing the method ```isAlive()``` from ```Player```. 
 
[Here is an example](/teaching/CS473-Fall2022/dynamic/PlayerTest.java_.txt) of such a test class, but I 
strongly advise you to try for yourself (it is a simple test and the hardest part is just to instantiate 
the objects).
 
After adding the new test, build ```jpacman.test``` again and run it with coverage. If your test does not 
have any errors, you should see the IntelliJ window showing the code coverage. Leave this window with the 
coverage information on as you may need it to answer the questions from the next task 
(or take a screenshot of it).

Task 2.1 - 15 points (5 points each)
====
Identify **three or more methods** in any java classes and write ```unit tests``` of those methods. 
**Remember to take screenshots of the test coverage before and after creating the unit tests.** 
**Since there are many methods in the project, I should not find almost all the group members of a given group attempting the same methods.** 
Discuss between the group mates what methods you will be writing unit tests for. 
A simple Google sheet having two columns would help get the group organised.

<table>
  <tr>
    <th style="border: 1px solid black;">Names</th>
    <th style="border: 1px solid black;">Fully Qualified Method Name</th>
  </tr>
  <tr>
    <td style="border: 1px solid black;">John Businge </td>
    <td style="border: 1px solid black;">src/main/java/nl/tudelft/jpacman/game/GameFactory.createSinglePlayerGame</td>
  </tr>
  <tr>
    <td style="border: 1px solid black;">John Businge </td>
    <td style="border: 1px solid black;">src/main/java/nl/tudelft/jpacman/board/BoardFactory.createBoard</td>
  </tr>

</table> 
 
<br/>

Task 3 -- JaCoCo Report on JPacman (10 points)
=====

The gradle build file provided in ```JPacman```, already has ```JaCoCo``` configured. Look at the folder 
```build/reports/jacoco/test/html```, right-click on the file ```index.html``` and select 
"Open in Browser". This is the coverage report from the ```JaCoCo``` tool. As you can see, ```JaCoCo``` shows not only 
line coverage but also branch coverage. Click on the ```level``` package, then on the ```Player``` class, 
and after that on any method. You will see the source code with color information on which branches are 
covered (or partially covered).
 
**Questions:** 
* Are the coverage results from ```JaCoCo``` similar to the ones you got from ```IntelliJ``` in the last task? Why so or why not?
* Did you find helpful the source code visualization from ```JaCoCo``` on uncovered branches?
* Which visualization did you prefer and why? ```IntelliJ```'s coverage window or ```JaCoCo```'s report?

**Write a report for Tasks 2.1 and Task 3. Name the report ```<your-names>_unitTesting.pdf>```**
Remember to include the **code snippets of your unit tests** for Tasks 2.1 in your report.
Make sure that your report is descriptive enough for me to follow without looking at your project code.

Task 4 -- Working with Python Test Coverage
=====
In this task, you will practice improving your test coverage in Python. You will generate a test coverage report and 
interpret the report to determine which lines of code do not have test cases, and writing test cases to cover those lines.

1. Clone the git project [Python Testing lab](https://github.com/johnxu21/test_coverage). Open the IDE, navigate to the directory ```test_coverage``` and run the command ```pip install -r requirements.txt```
2. You will do all your editing work in the file ```tests/test_account.py```.
3. Before writing any code, you should always check that the test cases are passing. 
   Otherwise, when they fail, you won’t know if you broke the code, or if the code was broken before you started.
  * run the ```nosetests``` and produce a ```coverage``` report to identify the lines that are missing code coverage:

```nosetests
  Name                 Stmts   Miss  Cover   Missing
--------------------------------------------------
models/__init__.py       6      0   100%
models/account.py       40     13    68%   26, 30, 34-35, 45-48, 52-54, 74-75
--------------------------------------------------
TOTAL                   46     13    72%
----------------------------------------------------------------------
Ran 2 tests in 0.349s
```

4. Starting with 72% test coverage. The goal is to reach 100%! Looking at the first missed line, 
line 26 in ```account.py``` to see if we can write a test case for it. To increase the test coverage, 
we first investigate line 26 in ```models/account.py```. This file is in the ```model``` 
package from the root of the repo. Look at the following code on lines ```25``` and ```26```.

```python
def __repr__(self):
    return '<Account %r>' % self.name
```
Notice that this method is one of the magic methods that is called to represent the class when 
printing it out. We will add a new test case in ```test_account.py``` that calls the ```__repr__()``` 
method on an Account.

```python
def test_repr(self):
    """Test the representation of an account"""
    account = Account()
    account.name = "Foo"
    self.assertEqual(str(account), "<Account 'Foo'>")
```

5. Run ```nosetests``` again to ensure line ```26``` is now covered through testing and to determine 
the next line of code for which you should write a new test case:

```angular2html
Name                 Stmts   Miss  Cover   Missing
--------------------------------------------------
models/__init__.py       6      0   100%
models/account.py       40     12    70%   30, 34-35, 45-48, 52-54, 74-75
--------------------------------------------------
TOTAL                   46     12    74%
----------------------------------------------------------------------
Ran 3 tests in 0.387s
```
Note that the overall test coverage has increased from 72% to 74% and the new report does not 
list line ``26`` in the Missing column. 

6. Next, let us look at the next line of code listed in the lines of code missing tests cases, line 
is ```30```. Examine this line in ```models/account.py``` to find out what that code is doing.

We will look at code of the entire function on lines ```28``` through ```30``` to see what it is 
doing.
```python
def to_dict(self) -> dict:
    """Serializes the class as a dictionary"""
    return {c.name: getattr(self, c.name) for c in self.__table__.columns}
```
Notice that this code is the ```to_dict()``` method. Now, let us add a new test case in ```test_account.py``` 
that executes the ```to_dict()``` method on an Account, and thereafter run ```nosetests``` again.

```python
def test_to_dict(self):
    """ Test account to dict """
    data = ACCOUNT_DATA[self.rand] # get a random account
    account = Account(**data)
    result = account.to_dict()
    self.assertEqual(account.name, result["name"])
    self.assertEqual(account.email, result["email"])
    self.assertEqual(account.phone_number, result["phone_number"])
    self.assertEqual(account.disabled, result["disabled"])
    self.assertEqual(account.date_joined, result["date_joined"])
```

```angular2html
Name                 Stmts   Miss  Cover   Missing
--------------------------------------------------
models/__init__.py       6      0   100%
models/account.py       40     11    72%   34-35, 45-48, 52-54, 74-75
--------------------------------------------------
TOTAL                   46     11    76%
----------------------------------------------------------------------
Ran 4 tests in 0.368s
```
Note that the overall test coverage increased from 74% to 76%. 

#### Your task - Getting coverage to 100% (20)
In this task to try to get the test coverage to close to 100% as possible. You will 
examine ```models/account.py``` on lines ```34-35```, ```45-48```, ```52-54```, ```74-75``` 
to find out what that code is doing.

**Add to your report of the previous tasks and include the code snippets for your test cases.**

Task 5 - TDD
=======
Test driven development (TDD) is an approach to software development in which you first write the 
test cases for the code you wish you had and then write the code to make the test cases pass.
In this Task, you will write test cases based on the requirements given to you, and then you 
will write the code to make the test cases pass.

1. You will clone and use the repo ([Python Testing lab](https://github.com/johnxu21/tdd)). Navigate to the ```tdd``` folder. If you did not already install the requirements, run the command ```pip install -r requirements.txt```
2. Open the IDE, navigate to the directory ```tdd```.
      * ```status.py``` -  has some HTTP error codes that we will use when we're checking our error codes
      *  ```setup.cfg``` - In case you have many files in the project, and you are only interested in focusing on a specific directory or file you are testing, so that ```nosetests``` only returns testing results for that file, e.g., ```cover-package=counter```
      * You will add test cases in ```test_counter.py```. Currently, the file contains only a doc string listing the requirements and no code.
3. You will be working with **HTTP methods** and **REST guidelines** you can take a read [here](https://restfulapi.net/http-methods/)
#### Creating a counter
You will start by implementing a test case to test creating a counter. Following REST API guidelines, create uses 
a PUT request and returns code ```200_OK``` if successful. Create a counter and then update it.
1. Write the following code in the file ```test_counter.py```. Run ```nosetests```. You should see an error ```ModuleNotFoundError```

```python
from unittest import TestCase

# we need to import the unit under test - counter
from src.counter import app 

# we need to import the file that contains the status codes
from src import status 

class CounterTest(TestCase):
    """Counter tests"""
```
2. Create a new file in the ```src``` directory called ```counter.py``` and run ```nosetests``` again. You should see an ```ImportError```, cannot find ```app```
3. Write the code below and run ```nosetests``` again. The tests should run with no error.
  
```python
from flask import Flask

app = Flask(__name__)
```

4. Let us write our first test case and run ```nosetests``` again. 
```python
    def test_create_a_counter(self):
        """It should create a counter"""
        client = app.test_client()
        result = client.post('/counters/foo')
        self.assertEqual(result.status_code, status.HTTP_201_CREATED)
```
This time we get <span style="color:red">**RED**</span> - ```AssertionError: 404 !=201```. 
I didn't find an endpoint called ```/counters```, so I can't possibly post to it." That's the next piece of 
code we need to go write.

5. Let's go to ```counters.py``` and create that endpoint. 

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
When we run ```nosetests``` again, we will have <span style="color:green">**GREEN**</span>.

## Duplicate names must return a conflict error code.
The second requirement is if the name being created already exists, return a 409 conflict.
* Since a lot of the code is a repeat we will <span style="color:blue">**REFACTOR**</span> 
the repetitive code into ```setUp``` function. Since ```self.client = app.test_client()``` that is
inside ```test_create_a_counter``` test case will be used by more than one test case, let us <span style="color:blue">**REFACTOR**</span>
it into the ```setUp``` function.

```python
def setUp(self):
  self.client = app.test_client()
```

* Let us now write the ``test_duplicate_a_counter`` as below. We create a counter called ``bar`` two times.
The second time we expect to get a ```HTTP_409_CONFLICT```. 

```python
def test_duplicate_a_counter(self):
  """It should return an error for duplicates"""
  result = self.client.post('/counters/bar')
  self.assertEqual(result.status_code, status.HTTP_201_CREATED)
  result = self.client.post('/counters/bar')
  self.assertEqual(result.status_code, status.HTTP_409_CONFLICT)
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
When we run ```nosetests``` again we should get the <span style="color:green">**GREEN**</span> phase.

## Your task (15 points)
You will implement the updating the counter by name following the TDD workflow (write test cases and 
write the code to make the test cases pass).
The test cases you will add to are in ```test_counter.py```, and the code you will add is in ```counter.py```. These are the only two files you will work with.
Following REST API guidelines, an update uses a ```PUT``` request and returns code ```200_OK``` if successful. 
Create a counter and then update it. 
You will implement the following requirements:

In ```test_counter.py```, create a test called ```test_update_a_counter(self)```. It should implement the following steps:
1. Make a call to Create a counter.
2. Ensure that it returned a successful return code.
3. Check the counter value as a baseline.
4. Make a call to Update the counter that you just created.
5. Ensure that it returned a successful return code.
6. Check that the counter value is one more than the baseline you measured in step 3.

When you run ```nosetests```, you should be in the <span style="color:red">**RED**</span> phase.

Next, in ```counter.py```, create a function called ```update_counter(name)```. 
It should implement the following steps:

1. Create a route for method ```PUT``` on endpoint ```/counters/<name>```.
2. Create a function to implement that route.
3. Increment the counter by 1.
3. Return the new counter and a ```200_OK``` return code.

Next, you will write another test case to read a counter. Following REST API guidelines, a read uses a 
```GET``` request and returns a ```200_OK``` code if successful. Create a counter and then read it. 
Here you should figure out the requirements for the test case as well as code you will put in the unit under test.

Add to your report of the previous tasks and detail the steps (red/green/refactor phases) you followed 
to implement the requirements. Include in your report the code snippets you wrote at every step as well as 
the exceptions you encountered while running ```nosetests```. 
**Make your report self-contained so that it is easy to follow without running your code**
 
Submitting the Assignment
=======
* Put a **link to your fork repository in the report**.
* create a folder on your local fork repository called ```jpacman```.
* create a branch on your local fork repository called ```jpacman_tests``` using the following command ```git branch jpacman_tests```.
* run the command ```git checkout jpacman_tests```
* copy your report--```<your-names>_unitTesting.pdf>``` and paste it in the folder ```jpacman```
* push the changes onto your remote fork repository.
* open a pull request on the ```main branch``` of the Team repository and write an appropriate title and body.
* one of the repository maintainers should integrate your contribution into the main branch.
* **for Tasks 4 & 5, only the report is required.**
* You should also submit your report on **Canvas**


