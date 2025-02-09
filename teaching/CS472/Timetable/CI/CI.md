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


## **Introduction**
This **Continuous Integration (CI) Lab** builds upon the work done in the **Testing Lab**. In this lab, you will extend the testing process by **enhancing existing test cases** with additional assertions and integrating **GitHub Actions** to automate test execution.  

CI ensures that all code changes are **continuously tested** and **validated** before being merged into the repository. You will work collaboratively, submitting **Pull Requests (PRs)** to incorporate your modifications while ensuring the test suite runs successfully in an **automated CI pipeline**.

## **Learning Outcomes**
By completing this lab, you will be able to:

- **Set up a GitHub Actions workflow** for Continuous Integration (CI).  
- **Automate test execution** for your repository using GitHub Actions.  
- **Enforce code quality** with Flake8 for Python linting.  
- **Extend test coverage** by adding meaningful assertions to existing tests.  
- **Resolve merge conflicts** and collaborate efficiently using GitHub.  
- **Submit a Pull Request (PR)** and ensure tests run successfully in CI.  

## **Repository Setup**
To begin, **one team member** should create a folder named `ci_lab` in the local copy of the team repository and add the necessary files. The rest of the team will pull the updates after they are merged.

1. **One team member** downloads the **starter files** from the [CI Lab repository](https://github.com/UNLV-CS472-672/CI) and places them into the `ci_lab` folder inside the team repository.
2. **Ensure `.gitignore` is included** to prevent committing unnecessary files like `.pyc`, `__pycache__/`, and environment-specific files.

## **Step 1: Setting Up GitHub Actions for Continuous Integration (CI)**

### **Overview**
In this step, you will create a **GitHub Actions workflow** to automatically **run tests and enforce code quality checks** whenever changes are pushed to the repository.

### **1. One Student Sets Up the `ci.yml` File in the Team Repository**
Only **one** student should create and set up the CI workflow file to prevent merge conflicts.

#### Steps for the Assigned Student:
- Create a new branch for the CI workflow setup:

```bash
   git checkout -b add-ci-workflow
```

- Create the workflow directory:

```bash
mkdir -p .github/workflows
```

- Copy the **ci.yaml** fall from the `CI_Lab` directory workflow configuration file:

```bash
cp ci_lab/ci.yml .github/workflows/
```
- Commit and push the branch:

```bash 
git add .github/workflows/ci.yml
git commit -m "Added initial GitHub Actions workflow"
git push origin add-ci-workflow
```

- Open a Pull Request to merge `add-ci-workflow` into the team repository’s main branch.

### **2. Verify That CI is Running**
Once the `ci.yml` file is merged into the team repository, confirm that GitHub Actions is running correctly:

- Go to your **team repository** on GitHub. 
- Click on the **"Actions"** tab. 
- You should see your **CI Workflow** running on the latest commit. 
- If successful, you will see a **green checkmark** indicating the workflow completed successfully.

#### **If There Is an Error**
- Click on the failed workflow run to **view the logs**.

## **3. All Other Team Members Pull the Latest Version**
Once the PR is merged, all other team members should pull the latest version from the team repository to get the `ci.yml` file:

```bash
git checkout main
git fetch upstream
git merge upstream/main
git push origin main #push to your fork
```

### **4. Each Team Member Should Understand the Workflow by Reviewing These Key Steps**
- **Triggers:** This workflow runs **on every push** and **pull request** to the `main` branch.
- **Job Name:** The job is named **`build`**, which runs on an **Ubuntu environment**.
- **Checkout Code:** The first step **checks out** the repository so the CI workflow has access to the files.
- **Set Up Python:** Ensures the workflow uses Python 3.9.
- **Install Dependencies:** Installs the required packages listed in `requirements.txt`.
- **Run Tests with Pytest:** Executes all unit tests and generates a coverage report.
- **Install Flake8**: Ensures that Flake8 is available in the CI environment.
- **Run Flake8 Linting**: Checks for:
  - **Syntax errors** (`E9`)
  - ⚠**Undefined names** (`F63`, `F7`, `F82`)
  - **General code style issues**

## **Step 2: Writing & Automating Your Test Case in CI**

Now that you have successfully configured **Continuous Integration (CI) with GitHub Actions**, your next task is to **extend test coverage** by adding new test cases that will be automatically executed in CI.

### **1. Pull Latest Changes Before Modifying Test Cases**
Before making changes to your assigned test case, ensure you have the latest version of the repository:

```bash
git checkout main
git fetch upstream
git merge upstream/main
git push origin main
```

### **2. Add Your Assertion to the Test Case**  

Each student has been assigned a specific assertion to add in the `tests/test_counter.py` file.  
Your assigned test case is already labeled in the file with:

#### **Key Points to Remember**
- You **do NOT** need to modify `counter.py` — the API is already implemented.  
- All test cases are already written — your task is to **add a missing assertion** to improve validation.  
- You must **submit a Pull Request (PR)** with your changes.  
- Work collaboratively — discuss assignments and resolve merge conflicts as needed.  

#### **Steps to Follow**
- **Ensure your repository is up-to-date** before making changes:
   ```bash
   git checkout main
   git fetch upstream
   git merge upstream/main
   git push origin main
   ```
   
- Create a new branch for your test case modification:
```bash
git checkout -b add-test-assertion
```

- Locate your assigned test case in `tests/test_counter.py`:
  - Find your assigned test case:
   - Look for the label **"Student 1"**, **"Student 2"**, etc.
   - Read the **test description** to understand its purpose.
   - Identify the **`TODO` comment**, which specifies the assertion you need to add.
- **Add the missing assertion** in the correct location within the test.
- **Run the tests locally** to ensure your assertion is correct:
 ```bash
 pytest --cov=src --cov-report=term-missing
```
- Coordinate within your group to ensure each student takes one labeled task.
- Commit and push your changes to your fork:
```bash
git add tests/test_counter.py
git commit -m "Added missing assertion for [Student #] test case"
git push origin add-test-assertion
```
- Submit a Pull Request to integrate your modification into the team repository.
 - Open a PR from your `add-test-assertion` branch to the team repository (`upstream/main`).
 - **Wait for CI to run before merging!**

#### **Verify CI Test Results**
- Go to your **team repository** on GitHub.
- Click the **"Actions"** tab.
- Find your **Pull Request** and check if all **CI tests passed**.
- If the **CI failed**, review the logs, fix the issue, and push your changes again.

---

#### **Resolve Merge Conflicts (If Any)**
- If you encounter a **merge conflict**, follow these steps to update your branch with the latest changes from `upstream/main`:

```bash
git checkout main
git fetch upstream # Fetch the latest changes from the team repository (`upstream/main`) without merging them yet.
git merge upstream/main
git push origin main
git checkout add-test-assertion
git merge main
```
- Manually resolve conflicts in test_counter.py before pushing again.
- Once resolved, commit and push the changes:
```bash
git add tests/test_counter.py
git commit -m "Resolved merge conflict in test_counter.py"
git push origin add-test-assertion
```
- Once your CI tests pass and there are no conflicts, your PR can be merged into the team repository.

## **Step 3. What to Include in Your Report**

### **Continuous Integration (CI) Lab Results**
- A link to your **Pull Request (PR)** for the CI Lab.
- A **copy of the assertion** you added to your assigned test case.
- A **brief explanation** of what your assertion does and how it improves test quality.
- A **summary of the CI results**, including:
  - Whether your test passed after the modification.
  - Any CI failures and how you fixed them.
  - Any additional improvements or refactoring needed.

### **Submission Instructions**
- Ensure your report is **clear and self-contained**, so it can be understood **without running your code**.  
- Upload your final report as a **PDF on Canvas**.