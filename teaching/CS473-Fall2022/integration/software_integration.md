---
layout: page
title: Software Integration
permalink: /teaching/Software-Reengineering/integration/
---

<form action="/teaching/Software-Reengineering/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>
<form action="/teaching/Software-Reengineering/metrics/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Metrics and Visualization" />
</form>
<form action="/teaching/Software-Reengineering/refactoring/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Refactoring Assistants" />
</form>
<form action="/teaching/Software-Reengineering/dynamic/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Dynamic Analysis: Testing" />
</form>
<form action="/teaching/Software-Reengineering/integration/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Software Integration" />
</form>
<form action="/teaching/Software-Reengineering/msr/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Mining Software Repositories" />
</form>
<form action="/teaching/Software-Reengineering/project/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Reengineering Project" />
</form>

<br/>
<br/>

Many modern software systems are created by forking an existing codebase. While most forks are short-lived and serve temporary collaboration needs, a smaller but more impactful subset evolve into long-lived forks, referred to here as software variants, that follow independent development trajectories. These variants allow customization and organizational control, but over time their structural and semantic divergence complicates the reuse of bug fixes or enhancements from each other Prior work with **PaReco**
([paper](https://dl.acm.org/doi/10.1145/3540250.3549112)) shows that reuse gaps often appear as missed 
opportunities (patch present in the source but absent in the target) or effort duplication (similar patch 
re‑implemented manually). Our extended tool, **[GACPD](https://github.com/unlv-evol/GACPD)**, builds on the 
**[PaReco](https://github.com/unlv-evol/PaReco)** tool with broader language support, 
faster token normalization, and developer-facing outputs to surface **candidate patches** worth reusing. 
When selecting what to integrate, apply **Most Valuable First** (OORP, p.29) to prioritize the highest‑impact 
patches, and **Keep It Simple** (OORP, p.37) to avoid unnecessary complexity in your plan.

Despite automated detection, structural divergence caused by refactorings (renames, moves, interface 
changes) can block direct reuse. **RePatch** ([paper](https://arxiv.org/pdf/2508.06718)) performs 
**refactoring‑aware patch integration** by aligning the source and target around detected refactorings, 
applying the patch, then replaying those refactorings so the target keeps its structure. Guard your work 
with **Tests: Your Life Insurance** (OORP, p.149), use **Write Tests to Understand** (OORP, p.179) when 
behavior is unclear, and **Grow Your Test Base Incrementally** (OORP, p.159) to expand coverage only where 
the integration touches. Keep adaptations minimal (again, **Keep It Simple**, p.37), focus on the immediate 
collaborators of the change, and document any manual decisions for review.


Materials & Tools Used for this Session
========
Lecture sides [here](../../../files/Integration.pdf)
IDEs  
* [PyCharm](https://www.jetbrains.com/academy/student-pack/)  
* [IntelliJ IDEA](https://www.jetbrains.com/idea/) – The **Ultimate Edition** is recommended, as it includes built-in support for generating UML diagrams directly from your code.

Repositories
* Source repository: [apache/kafka](www.github.com/apache/kafka)
* Target repository: [linkedin/kafka](www.github.com/linkedin/kafka)

Setup / Preparation
===============
In this lab you will play with two very related tools: [GACPD](https://github.com/unlv-evol/GACPD) and [RePatch](https://github.com/Software-Reengineering/RePatch)

## Task 1 – Identifying a Missed Opportunity with GACPD

In this task, you will use **GACPD** to detect and validate a **Missed Opportunity (MO)** patch between two related repositories:  
- **Source (Mainline):** `apache/kafka`  
- **Target (Divergent fork):** `linkedin/kafka`  

We have already identified a candidate patch from **Apache Kafka Pull Request #13386** that appears in the mainline repository but not in the divergent fork.  
Your goal is to:  
1. **Run GACPD** to detect the patch.  
2. **Read and understand the patch’s intent.**  
3. **Verify the results** by inspecting both repositories.  

Following the *Most Valuable First* pattern (p.29), we begin with a high-impact MO that, if integrated, will improve parity and stability between variants.

---

### Step-by-Step Instructions

#### **1. Install GACPD**
Follow the installation instructions in the [GACPD README](https://github.com/unlv-evol/GACPD).  
Make sure you can run Jupyter notebooks in your environment.

---

#### **2. Run the analysis**
1. Open the [`OnePR.ipynb`](https://github.com/unlv-evol/GACPD/blob/main/OnePR.ipynb) file in the root of the GACPD repository.  
2. Execute the notebook cells as instructed.  
3. Ensure the notebook is configured to analyze **PR #13386** from `apache/kafka`.

`example.individual_pr_check(13386)`

This step applies the *Detecting Duplicated Code pattern (p.223)* — GACPD uses similarity analysis to find duplicated or nearly duplicated changes across repositories.

---

#### **3. View the GACPD output**
When the analysis finishes, navigate to the output folder:  
```Results/Repos_files/1/<PR-number>/MO/<path-to-source-file>/results.txt```
This file contains the file paths in both repositories that you can use for manual inspection.

This file contains the file paths in both repositories that you can use for manual inspection.
Here, we apply the *Compare Code Mechanically pattern (p.227)* — use automated, tool-driven comparison before diving into manual review.

---

#### **4. Read and understand the patch**
Open Apache Kafka Pull Request [#13386](https://github.com/apache/kafka/pull/13386)

Read the PR description and discussion to understand:
* What the patch does (functional change or improvement).
* Why it was made (e.g., bug fix, performance, metrics/observability).
* Why it matters for both the source (`apache/kafka`) and the target (`linkedin/kafka`).

Pattern cue — *Most Valuable First (OORP, p.29)*: articulate the value/impact of this change before investing further effort, so you focus integration work on the highest‑benefit patches first.

#### **5. Verify the Missed Opportunity**
1. **Open the source repository** (`apache/kafka`) and navigate to the file path shown in the report or `results.txt`.  
   - Confirm that the hunk appears in the PR’s changes.  
2. **Open the target repository** (`linkedin/kafka`) and navigate to the same file path.  
   - Check whether the hunk exists in the code.  
   - If it is missing, it confirms the **MO classification** from GACPD.

---

## Task 2 – Integrating the Missed Opportunity with RePatch
In this task, you will use **RePatch** to integrate **MO** patch identified in Task 1 between the two related repositories:  
 
Your goal is to:  
1. **Run RePatch** to integrate the patch.  
2. **Verify the results** by inspecting the backend database.  

---

### Step-by-Step Instructions

#### **1. Install RePatch**
Follow the installation instructions in the [RePatch README](https://github.com/Software-Reengineering/RePatch).  

---

#### **2. Run the Integration Pipeline**
- Open and build the project in IntelliJ IDEA.
- For this lab, the pipeline is already preconfigured to analyze **PR #13386** from apache/kafka. Simply run the project and wait for the integration to finish.
- For the **project assignments**, you will need to configure `RePatch` to analyze different PRs (four in total).
  - The PR configuration is stored in the **src/main/resources/complete_data** directory (see README, section Configuring PRs).
  - To switch to a new PR, update the configuration file(s) in the **src/main/resources/sample_data** with the PR number and repository details provided in your project instructions.
  - Rebuild and rerun `RePatch` with the updated settings.

---

#### **3. View RePatch output**

When the integration finishes, inspect the results in MySQL.

* **How to connect:** Use any MySQL client—e.g., MySQL Workbench (GUI), the MySQL CLI, or **phpMyAdmin** (included in the Docker setup for RePatch).
* **What to look at:** The key table is `merge_result`, which records how **RePatch** reduced or resolved merge conflicts when `git cherry-pick` failed. Other tables include useful metadata and diagnostics (e.g., projects, patches, refactorings, conflicting files, conflict blocks).
* For setup details, see the lab project’s README.

**Quick start (SQL):**

{% highlight sql %}
-- List databases
SHOW DATABASES;

-- Switch to the RePatch database
USE refactoring_aware_integration_repatch;

-- See available tables
SHOW TABLES;

-- Inspect the structure of a table
DESCRIBE merge_result;

-- Preview rows from a specific table
SELECT * FROM merge_result LIMIT 50;
{% endhighlight %}

**Template query (replace the placeholder):**

```SELECT * FROM <table_name> LIMIT 50;```


<!-- #### **3. View the output of RePatch**
When the integration finishes, navigate to the MySQL database to inspect the result. There are several tools you can use to connect to the database including; MySQL Workbench (GUI) and MySQL CLI. If you are using the Docker installation of `RePatch`, you alreay have phpMyAdmin configured for you. A detailed information is added in the README of the lab project repository.

 Explore `merge_result` table, which records how `RePatch` reduced or resolved merge conflicts when git cherry-pick failed. The other tables also contain useful metadata and diagnostics such as refactorings, conflicting files, conflict blocks, etc., so give them a look as well. Run the SQL code below - replace **table_name** which the actually table you would like to inspect;

```SELECT * FROM table_name;``` -->

 ---

## Task 4 – Writing Tests for Integrated Changes

Up to now, we have used RePatch to integrate a missed opportunity patch from **Apache Kafka PR #13386** into the target repository. However, integration at the syntactic level is not enough — we also need to ensure that the change behaves correctly in its new context.

In this task, you will write a **missing test** for the integrated patch.

---

### Step-by-Step Instructions

1. Inspect the code hunk from PR #13386 that was integrated into the target repository.  
2. Identify the behavior or functionality that the hunk is meant to enforce (e.g., offset commit logic, logging, or metrics).  
3. Write a **unit test or integration test** in the target repository that exercises this functionality.  
   - Use existing test files as templates.  
   - Place the new test alongside related tests in the appropriate test suite.  
4. Run the test suite and verify that your new test passes.  
   - If it fails, investigate whether the integration requires additional adaptations.  

---

### Reflection Questions (for quiz prep)
- Did your test confirm that the patch works correctly in the target repository?  
- Could you imagine cases where a patch integrates syntactically but still breaks functionality?  
- How do tests strengthen confidence in patch reuse across software variants?  
