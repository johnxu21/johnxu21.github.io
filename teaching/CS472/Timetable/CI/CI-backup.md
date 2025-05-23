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

## **🎯 Learning Outcomes**
By completing this lab, you will be able to:
✔️ **Set up a GitHub Actions workflow** for Continuous Integration (CI).  
✔️ **Automate test execution** for your repository using GitHub Actions.  
✔️ **Enforce code quality** with Flake8 for Python linting.  
✔️ **Extend test coverage** by adding new test cases.  
✔️ **Resolve merge conflicts** and collaborate efficiently using GitHub.
---

## **📁 Repository Setup**
To begin, download the **starter files** from the [CI Lab repository](https://github.com/UNLV-CS472-672/CI) and follow the setup instructions.

In this lab, you will kick off from where you stopped in the [Testing lab](../dynamic_analysis)
and build a GitHub Action Continuous Integration pipeline.
This pipeline will run automatically when you push/commit your code to the GitHub 
repository based on the events described in the workflow.

You will push changes to your cloned repo at the end of this lab. This requires you 
to authenticate with GitHub using a ```personal access token``` (ref. [Git & GitHub lab](../Git_and_GitHub/)).

Task 1: (5 points)
-------
1. In this lab, we will only focus on the TDD. You will use the code you cloned and updated ([Python Testing lab](https://github.com/UNLV-CS472-672/tdd))
2. On the root directory of your repo, create the directory structure ```.github/workflows/``` and create a file called ```workflow.yml```. You can use the two commands below.
```
mkdir -p .github/workflows
touch .github/workflows/workflow.yml
```
3. **Create a Workflow**: Every workflow starts with a name. The name will be displayed on the Actions page and on any badges. Give your workflow the name ```CI workflow``` by adding a ```name:``` tag as the first line in the file.
4. **Add Event Triggers**: Event triggers define which events can cause the workflow to run. You will use the ```on:``` tag to add the following events: 1) Run the workflow on every push to the main branch and 2) Run the workflow whenever a pull request is created to the main branch.
  * Add the ```on:``` keyword to the workflow at the same level of indentation as the ```name:```
  * Add a ```push:``` event as the first event that can trigger the workflow. 
    This is added as the child element of ```on:``` so it must be indented under it.
  * Add the ```"main"``` branch to the push event. You want the workflow to start every 
    time somebody pushes to the main branch. This also includes merge events. You do 
    this by using the branches: keyword followed by a list of branches either as 
    ```[]``` or ```-```
  * Add a ```pull_request:``` event similar to the push event you just finished. It should be 
    triggered whenever the user makes a pull request on the main branch.
5. **Add a Job**: You will now add a job called build to the workflow file. This job will run on the ```ubuntu-latest``` runner. Remember, a job is a collection of steps that are run on the events you added in the previous step.
  * Add the ```jobs:``` section to the workflow at the same level of indentation as the 
   ```name``` (i.e., no indent).
  * Next, you need to name the job. Name your job ```build:``` by adding a new line under the 
    ```jobs:``` section.
  * Finally, you need a runner. Tell GitHub Actions to use the ```ubuntu-latest``` runner for 
    this job. You can do this by using the ```runs-on:``` keyword.
6. **Target Python 3.9**: It is important to consistently use the same version of dependencies and operating system for all phases of development including the CI pipeline. This project was developed on Python 3.9, so you need to ensure that the CI pipeline also runs on the same version of Python. You will accomplish this by running your workflow in a container inside the GitHub action.
  * Add a ```container:``` section under the runs-on: section of the build job, and 
    tell GitHub Actions to use ```python:3.9-slim``` as the image.
7. Save and commit your changes to your repository.

When you click on ```Actions``` tab in your repository, you should be able to see screen like the one below.

<img src="/teaching/CS472/Timetable/CI/task1.jpeg" alt="WorkflowWithNoSteps" style="width:612px;height:114px;" align="center">

Task 2 (5 points)
-----
In this task, you will continue building the Continuous Integration pipeline by setting up the steps under job in your workflow. As a result, your application shall be automatically built and tested when you commit your code to the GitHub repository.
1. Add the ```steps:``` section under ```build``` job in the workflow file.
2. Add the checkout step as the first step. Give it the ```name:``` ```Checkout``` and call the 
action ```actions/checkout@v3``` by using the ```uses:``` keyword.
3. **Install Dependencies**: Now that you have checked out the code, the next step is to install the dependencies. This application uses pip, the Python package manager, to install all the dependencies from the PyPI package. The ```pip``` command refers to the ```requirements.txt``` file for the list of dependencies. The ```python:3.9-slim``` container you are using already has the pip package manager installed. The commands that you will use in this step are:
    
  ```
    python -m pip install --upgrade pip
    pip install -r requirements.txt
  ```
  * Add a new named step after the checkout step. Name this step ```Install dependencies```.
  * Next, you want to run the commands to update the package manager ```pip``` and then install the dependencies. Since there are two commands, you can run these inline using the ```run:``` keyword with the pipe ```|``` operator.
4. **Lint with flake8**: It is always a good idea to add quality checks to your CI pipeline. This is especially true if you are working on an open source project with many contributors. This makes sure that everyone who contributes is following the same style guidelines.
<br/><br/>
The next step is to use ```flake8``` to lint the source code. Linting is checking your code for syntactical and stylistic issues. Some examples are line spacing, using spaces or tabs for indentation, locating uninitialized or undefined variables, and missing parentheses. The ```flake8``` library was installed as a dependency in the ```requirements.txt``` file.
<br/><br/>
The flake8 commands take a few parameters. Now, take a look at the command and the parameters:

    ```angular2html
    flake8 src --count --select=E9,F63,F7,F82 --show-source --statistics
    ```
This command will run ```flake8``` for the src folder of your repository. By adding the following options, you customize the linting process:
  * ```--count``` : shows the count of all warnings and errors in the result of the command
  * ```--select=E9,F63,F7,F82``` : limits the checks to syntax errors
  * ```--show-source``` : adds the actual line number where the error/warning is found
  * ```--statistics``` : shows the count of each type of error and warning in the result
  
    ```angular2html
    flake8 src --count --max-complexity=10 --max-line-length=127 --statistics
    ``` 
    Unlike the first command that checks for syntax errors only, the second command will run all the available checks on the src folder of your repository.
  * Add a new named step after the ```Install dependencies``` step. Call this step ```Lint with flake8```.
  * Next, you want to run the ```flake8``` commands to lint your code. The commands are explained in detail above
    ```angular2html
    flake8 src --count --select=E9,F63,F7,F82 --show-source --statistics
    flake8 src --count --max-complexity=10 --max-line-length=127 --statistics
    ```
    You can run inline commands using the ```run:``` keyword with the pipe ```|``` operator.
  * **In the file ```requirements.txt``` the dependency for ```flake8``` is missing. Include ```flake8```, otherwise CI build will not succeed.**

1. **Test Code Coverage with pytests**: You will use pytest in this step to unit test the source code. Pytest is configured via the included ```pytest.ini``` file to automatically include the flags ```-–with-spec``` and ```–-spec-color``` so that red-green-refactor is meaningful. If you are in a command shell that supports colors, passing tests will be <span style="color:green">**green**</span> and failing tests will be <span style="color:red">**red**</span>.
   <br/><br/>
Pytest is also configured to automatically run the coverage tool, and you should see a percentage of coverage report at the end of your tests.
  * Add a new named step after the ```Lint with flake8``` step. Call this step ```Run unit tests with pytests```.
  * Next, you want to run the ```pytests``` command to test your code and report on code coverage.
    ```angular2html
    pytest -v --tb=short --color=yes --cov=src --cov-report=term-missing
    ```
    Since you are running a single command, you do not have to use the pipe ```|``` operator with ```run```.
1. **Push Code to GitHub**.

When you click on ```Actions``` tab in your repository, and then click on the latest workflow run (in green). You should be able to see screen like the one below.

<img src="/teaching/CS472/Timetable/CI/task2.png" alt="CompeteWorkflow" style="width:1035px;height:172px;" align="center">

<img src="/teaching/CS472/Timetable/CI/task2_2.png" alt="CompeteWorkflow" style="width:1601px;height:353px;" align="center">

If the CI build did not succeed, you can click and see where a problem could have occurred, then fix it locally and push again.

Clicking on ```Run unit tests with pytest```, you should be able to see the screen below. 

Fig 4: CI builds
<img src="/teaching/CS472/Timetable/CI/task2_3.png" alt="CompeteWorkflow" style="width:727px;height:567px;" align="center">

* From the image above, we can see that there are three ```Test Cases``` for the ```counter.py``` file. These are the ```Test Cases``` you were required to write in the [Testing lab](../dynamic_analysis). In this lab, you will write one more test case, using the red/green/refactor workflow, and push the code in your repository. You should be able to see that the fourth ```Test Cases``` turns <span style="color:green">**GREEN**</span> in your CI builds.

**You will write a test case to delete a counter. (10 points)**

Per REST API guidelines, a delete uses a ```DELETE``` request and returns a ```204_NO_CONTENT``` code if successful. Create a function that deletes the counter that matches the specified name.

Like in the [Testing Lab](../dynamic_analysis), detail the phases (red/green/refactor) you followed to implement the requirements. Include in your report the code snippets you wrote at every step as well as the exceptions you encountered while running pytests. **Make your report self-contained so that it is easy to follow without running your code**.

**Remember to commit your code**.

Submitting the Assignment
==========================
* Write a report for all the tasks. Include a link to your GitHub repository at the start of the report.
* Make sure that your repository is public so that we are able to access repository.
* To show that you were able to complete the tasks. Include screenshots for each task in your report. The screenshots should include the address bar of the browser so that we are able to see repo name.
* Submit your report on **Canvas**