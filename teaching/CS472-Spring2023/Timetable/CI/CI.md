---
layout: page
title: CS472 - CI - Using GitHub Actions - Setting up workflow
permalink: /teaching/CS472-Spring2023/Timetable/CI/
---

<div class="main-component">
<form action="/teaching/CS472-Spring2023/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>
<form action="/teaching/CS472-Spring2023/study_material/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Study Material" />
</form>
<form action="/teaching/CS472-Spring2023/Timetable/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Timetable" />
</form>
<form action="/teaching/CS472-Spring2023/Exam/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Exam" />
</form>
<form action="/teaching/CS472-Spring2023/project/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Project" />
</form>
</div>
<br/>

Labs
=======
<div class="main-component">
<form action="/teaching/CS472-Spring2023/Timetable/Git_and_GitHub/">
    <input type="submit" style="background-color:#008CBA;float:left; color:white;width:130px;
height:30px;" value="Git & GitHub" />
</form>
<form action="/teaching/CS472-Spring2023/Timetable/dynamic_analysis/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="Testing" />
</form>
<form action="/teaching/CS472-Spring2023/Timetable/CI/">
    <input type="submit" style="background-color:firebrick;float:left;color:white;width:130px;
height:30px;" value="CI" />
</form>
</div>

<br/>
<br/>

### **This individual assignment is due **

In this lab, you will build a GitHub Action Continuous Integration pipeline.
This pipeline will run automatically when you commit your code to the GitHub 
repository based on the events described in the workflow.

Task 1:
-------
1. Clone my repository [CI repository](https://github.com/johnxu21/CI-lab). 
Once you have cloned the repository, change to the directory named ```CI-lab```.
You can list the contents of the repository using the command ```ls -l```.
2. Create the directory structure ```.github/workflows``` and create a file called ```workflow.yml```.
```
mkdir -p .github/workflows
touch .github/workflows/workflow.yml
```
3. **Create a Workflow**: Every workflow starts with a name. The name will be displayed on the Actions page 
and on any badges. Give your workflow the name ```CI workflow``` by adding a ```name:``` 
tag as the first line in the file.
4. **Add Event Triggers**: Event triggers define which events can cause the workflow to 
run. You will use the ```on:``` tag to add the following events: 1) Run the workflow on 
every push to the main branch and 2) Run the workflow whenever a pull request is created to the main branch.
  * Add the ```on:``` keyword to the workflow at the same level of indentation as the ```name:```
  * dd ```push:``` event as the first event that can trigger the workflow. 
    This is added as the child element of ```on:``` so it must be indented under it.
  * Add the ```"main"``` branch to the push event. You want the workflow to start every 
    time somebody pushes to the main branch. This also includes merge events. You do 
    this by using the branches: keyword followed by a list of branches either as 
    ```[]``` or ```-```
  * Add a ```pull_request:``` event similar to the push event you just finished. It should be 
    triggered whenever the user makes a pull request on the main branch.
5. **Add a Job**: You will now add a job called build to the workflow file. This job will 
run on the ```ubuntu-latest``` runner. Remember, a job is a collection of steps that are run on 
the events you added in the previous step.
  * Add the ```jobs:``` section to the workflow at the same level of indentation as the 
   ```name``` (i.e., no indent).
  * Next, you need to name the job. Name your job ```build:``` by adding a new line under the 
    ```jobs:``` section.
  * Finally, you need a runner. Tell GitHub Actions to use the ```ubuntu-latest``` runner for 
    this job. You can do this by using the ```runs-on:``` keyword.
6. **Target Python 3.9**: It is important to consistently use the same version of 
dependencies and operating system for all phases of development including the CI 
pipeline. This project was developed on Python 3.9, so you need to ensure that the 
CI pipeline also runs on the same version of Python. You will accomplish this by 
running your workflow in a container inside the GitHub action.
  * Add a ```container:``` section under the runs-on: section of the build job, and 
    tell GitHub Actions to use ```python:3.9-slim``` as the image.
7. Save and commit your changes to your forked repository.

When you click on ```Actions``` tab in your repository, you should be able to see screen like the one below.

<img src="/teaching/CS472-Spring2023/Timetable/CI/task1.jpeg" alt="WorkflowWithNoSteps" style="width:612px;height:114px;" align="center">

Task 2
-----
In this task, you will continue building the Continuous Integration pipeline by setting up the 
steps under job in your workflow. As a result, your application shall be automatically built 
and tested when you commit your code to the GitHub repository.
1. Add the ```steps:``` section under ```build``` job in the workflow file.
2. Add the checkout step as the first step. Give it the ```name:``` ```Checkout``` and call the 
action ```actions/checkout@v3``` by using the ```uses:``` keyword.
3. **Install Dependencies**: Now that you have checked out the code, the next step is to install 
the dependencies. This application uses pip, the Python package manager, to install all the 
dependencies from the PyPI package. The ```pip``` command refers to the ```requirements.txt``` file for the 
list of dependencies. The ```python:3.9-slim``` container you are using already has the pip package 
manager installed. The commands that you will use in this step are:
    
   ```
    python -m pip install --upgrade pip
    pip install -r requirements.txt
    ```
  * Add a new named step after the checkout step. Name this step ```Install dependencies```.
  * Next, you want to run the commands to update the package manager ```pip``` and then install the 
dependencies. Since there are two commands, you can run these inline using the ```run:``` 
keyword with the pipe ```|``` operator.
4. **Lint with flake8**: It is always a good idea to add quality checks to your CI pipeline. 
This is especially true if you are working on an open source project with many contributors. 
This makes sure that everyone who contributes is following the same style guidelines.
<br/><br/>
    The next step is to use ```flake8``` to lint the source code. Linting is checking your code for 
syntactical and stylistic issues. Some examples are line spacing, using spaces or tabs for 
indentation, locating uninitialized or undefined variables, and missing parentheses. The ```flake8``` 
library was installed as a dependency in the ```requirements.txt``` file.
<br/><br/>
The flake8 commands take a few parameters. Now, take a look at the command and the parameters:

    ```angular2html
    flake8 service --count --select=E9,F63,F7,F82 --show-source --statistics
    ```
    This command will run ```flake8``` for the service folder of your repository. By adding the following 
    options, you customize the linting process:
    * ```--count``` : shows the count of all warnings and errors in the result of the command
    * ```--select=E9,F63,F7,F82``` : limits the checks to syntax errors
    * ```--show-source``` : adds the actual line number where the error/warning is found
    * ```--statistics``` : shows the count of each type of error and warning in the result
      ```angular2html
      flake8 service --count --max-complexity=10 --max-line-length=127 --statistics
      ``` 
    Unlike the first command that checks for syntax errors only, the second command will run all 
    the available checks on the service folder of your repository.
  * Add a new named step after the ```Install dependencies``` step. Call this step ```Lint with flake8```.
  * Next, you want to run the ```flake8``` commands to lint your code. The commands are explained in 
    detail above
    ```angular2html
    flake8 service --count --select=E9,F63,F7,F82 --show-source --statistics
    flake8 service --count --max-complexity=10 --max-line-length=127 --statistics
    ```
    You can run inline commands using the ```run:``` keyword with the pipe ```|``` operator.
5. **Test Code Coverage with nosetests**: You will use nose in this step to unit test the source code. 
   Nose is configured via the included setup.cfg file to automatically include the flags –with-spec 
   and –spec-color so that red-green-refactor is meaningful. If you are in a command shell that 
   supports colors, passing tests will be green and failing tests will be red.
   <br/><br/>
   Nose is also configured to automatically run the coverage tool, and you should see a percentage 
   of coverage report at the end of your tests.
  * Add a new named step after the ```Lint with flake8``` step. Call this step ```Run unit tests with nose```.
  * Next, you want to run the ```nosetests``` command to test your code and report on code coverage.
    ```angular2html
    nosetests -v --with-spec --spec-color --with-coverage --cover-package=app
    ```
    Since you are running a single command, you do not have to use the pipe ```|``` operator with ```run```.
6. **Push Code to GitHub**.

When you click on ```Actions``` tab in your repository, you should be able to see screen like the one below.

<img src="/teaching/CS472-Spring2023/Timetable/CI/task2.jpeg" alt="CompeteWorkflow" style="width:1035px;height:150px;" align="center">

<img src="/teaching/CS472-Spring2023/Timetable/CI/task2_2.jpeg" alt="CompeteWorkflow" style="width:1601px;height:300px;" align="center">






   








