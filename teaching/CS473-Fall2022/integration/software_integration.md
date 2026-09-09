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

Many modern software systems are created by forking an existing codebase. While most forks are short-lived and
serve temporary collaboration needs, a smaller but more impactful subset evolves into long-lived forks, referred
to here as **software variants**, that follow independent development trajectories. These variants allow
customization and organizational control, but over time their structural and semantic divergence complicates the
reuse of bug fixes or enhancements between them.

Prior work with **PaReco** ([paper](https://dl.acm.org/doi/10.1145/3540250.3549112)) shows that reuse gaps often
appear as **missed opportunities** (a patch present in the source but absent in the target) or **effort
duplication** (a similar patch re-implemented manually). Our extended tool,
**[GACPD](https://github.com/unlv-evol/GACPD)**, builds on **[PaReco](https://github.com/unlv-evol/PaReco)** with
broader language support, faster token normalization, and developer-facing outputs that surface **candidate
patches** worth reusing. **[MOVis](https://github.com/unlv-evol/MOVis)** is the front-end UI for GACPD that helps
you visualize those results.

Even with automated detection, structural divergence caused by refactorings (renames, moves, interface changes)
can block direct reuse. **RePatch** ([paper](https://arxiv.org/pdf/2508.06718)) performs **refactoring-aware
patch integration**: it aligns the source and target around the detected refactorings, applies the patch, and then
replays those refactorings so that the target keeps its own structure.

**In this session you will:**

* use MOVis to detect and verify a missed opportunity between two variants of Apache Kafka;
* use RePatch to integrate that patch into the divergent fork and inspect the results;
* write a test that confirms the integrated patch behaves correctly in its new context.

Materials & Tools Used for this Session
========

**Slides**

* [Software Integration (PDF)](../../../files/Integration.pdf)

**IDEs**

* [PyCharm](https://www.jetbrains.com/pycharm/) -- used to run MOVis.
* [IntelliJ IDEA](https://www.jetbrains.com/idea/) -- used to build and run RePatch. The **Ultimate Edition** is
  recommended, as it includes built-in support for generating UML diagrams directly from your code.
  Both are free for students through the [JetBrains Student Pack](https://www.jetbrains.com/academy/student-pack/).

**Repositories**

* Source repository (mainline): [apache/kafka](https://github.com/apache/kafka)
* Target repository (divergent fork): [linkedin/kafka](https://github.com/linkedin/kafka)

**Tools**

* [MOVis](https://github.com/unlv-evol/MOVis) -- front-end for GACPD; detects candidate patches for reuse.
* [RePatch](https://github.com/Software-Reengineering/RePatch) -- refactoring-aware patch integration.

**Book**

* [Object-Oriented Reengineering Patterns](http://scg.unibe.ch/download/oorp/) (OORP)
  (_Note: OORP, p.xx refers to a page in the pdf version of this book_)

<br/>

Setup / Preparation
===============

In this lab you will work with two closely related tools:
[MOVis](https://github.com/unlv-evol/MOVis) and
[RePatch](https://github.com/Software-Reengineering/RePatch). Install each one by following its README; the
per-task instructions below tell you when you need it.

When selecting what to integrate, apply "**Most Valuable First**" (OORP, p.29) to prioritize the highest-impact
patches, and "**Keep It Simple**" (OORP, p.37) to avoid unnecessary complexity in your plan. Guard your work with
"**Tests: Your Life Insurance**" (OORP, p.149). Keep adaptations minimal, focus on the immediate collaborators of
the change, and document any manual decisions for review.

> **Tip:** take screenshots while you work. You will need evidence of tool usage for the
> [Intermediate Report](/teaching/Software-Reengineering/project/) later in the semester.

<br/>

Task 1: Identifying a Missed Opportunity with MOVis
=========

In this task, you will use **MOVis** to detect and validate a **Missed Opportunity (MO)** patch between two
related repositories:

* **Source (mainline):** `apache/kafka`
* **Target (divergent fork):** `linkedin/kafka`

We have already identified a candidate patch from **Apache Kafka pull request #13386** that appears in the
mainline repository but not in the divergent fork. Your goal is to:

1. **Run MOVis** to detect the patch.
2. **Read and understand the patch's intent.**
3. **Verify the result** by inspecting both repositories.

### 1. Install MOVis

Follow the installation instructions in the [MOVis README](https://github.com/unlv-evol/MOVis). Make sure you can
run Jupyter notebooks in your environment.

### 2. Run the analysis

1. Select the "**One PR**" option in the toolbox.
2. Fill out all the data needed, except for the PR to be executed (that comes in the next step).
3. Analyze **PR #13386** from `apache/kafka`.

### 3. View the MOVis output

When the analysis finishes, open "**View Previous Results**" and select your project root name. This view contains
the file paths in both repositories, which you will use for manual inspection.

### 4. Read and understand the patch

Open Apache Kafka pull request [#13386](https://github.com/apache/kafka/pull/13386) and read its description and
discussion to understand:

* what the patch does (functional change or improvement);
* why it was made (e.g., bug fix, performance, metrics/observability);
* why it matters for both the source (`apache/kafka`) and the target (`linkedin/kafka`).

### 5. Verify the missed opportunity

1. **Open the source repository** (`apache/kafka`) and navigate to the file path shown in the report or
   `results.txt`. Confirm that the hunk appears in the PR's changes.
2. **Open the target repository** (`linkedin/kafka`) and navigate to the same file path. Check whether the hunk
   exists in the code. If it is missing, that confirms the **MO classification** made by GACPD.

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **Most Valuable First** *(p.29)* -- We begin with a high-impact missed opportunity that, if integrated, improves
  parity and stability between the variants. Articulate the value of the change before investing further effort.
- **Detecting Duplicated Code** *(p.223)* -- GACPD uses similarity analysis to find duplicated or nearly
  duplicated changes across repositories.
- **Compare Code Mechanically** *(p.227)* -- Use automated, tool-driven comparison before diving into manual
  review.

<br/>

Task 2: Integrating the Missed Opportunity with RePatch
=========

In this task, you will use **RePatch** to integrate the MO patch identified in Task 1 into the target repository.
Your goal is to:

1. **Run RePatch** to integrate the patch.
2. **Verify the result** by inspecting the backend database.

### 1. Install RePatch

Follow the installation instructions in the
[RePatch README](https://github.com/Software-Reengineering/RePatch).

### 2. Run the integration pipeline

* Open and build the project in IntelliJ IDEA.
* For this lab, the pipeline is already preconfigured to analyze **PR #13386** from `apache/kafka`. Simply run the
  project and wait for the integration to finish.
* For the **project assignments**, you will need to configure RePatch to analyze different PRs (four in total).
  * The PR configuration data lives under `src/main/resources/` -- the repository ships a `complete_data/`
    directory (real-world patch/project integration data) and a `sample_data/` directory (sample integration
    scenarios). Check the README for which one your assignment uses.
  * To switch to a new PR, update the configuration file(s) with the PR number and repository details given in
    your project instructions.
  * Rebuild and rerun RePatch with the updated settings.

### 3. View the RePatch output

When the integration finishes, inspect the results in MySQL.

* **How to connect:** use any MySQL client -- e.g., MySQL Workbench (GUI), the MySQL CLI, or **phpMyAdmin**
  (included in the Docker setup for RePatch).
* **What to look at:** the key table is `merge_result`, which records how RePatch reduced or resolved merge
  conflicts when `git cherry-pick` failed. The other tables hold useful metadata and diagnostics (projects,
  patches, refactorings, conflicting files, conflict blocks).
* For setup details, see the lab project's README.

**Quick start (SQL):**

```sql
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
```

To inspect any other table, replace the placeholder below:

```sql
SELECT * FROM <table_name> LIMIT 50;
```

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **Keep It Simple** *(p.37)* -- Avoid unnecessary setup complexity; stick to the minimal environment needed to
  run the integration.
- **Most Valuable First** *(p.29)* -- Start with the preselected high-impact PR before generalizing to others.
- **Compare Code Mechanically** *(p.227)* -- Rely on automated, tool-driven alignment before manual inspection.
- **Tests: Your Life Insurance** *(p.149)* -- Even after an automated integration, confirm correctness through
  testing (which is exactly what Task 3 is about).

<br/>

Task 3: Writing Tests for the Integrated Change
=========

So far we have used RePatch to integrate a missed opportunity patch from **Apache Kafka PR #13386** into the
target repository. However, integration at the syntactic level is not enough -- we also need to make sure that
the change behaves correctly in its new context. In this task, you will write the **missing test** for the
integrated patch.

1. Inspect the code hunk from PR #13386 that was integrated into the target repository.
2. Identify the behavior that the hunk is meant to enforce (e.g., offset commit logic, logging, or metrics).
3. Write a **unit test or integration test** in the target repository that exercises this behavior.
   * Use existing test files as templates.
   * Place the new test alongside related tests in the appropriate test suite.
4. Run the test suite and verify that your new test passes.
   * If it fails, investigate whether the integration requires additional adaptations.

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **Tests: Your Life Insurance** *(p.149)* -- Tests protect against regressions and confirm the correctness of the
  integration.
- **Write Tests to Understand** *(p.179)* -- Writing the test clarifies what the patch is supposed to do.
- **Grow Your Test Base Incrementally** *(p.159)* -- Add tests around the integrated patch instead of rewriting
  the whole suite.
- **Study the Exceptional Entities** *(p.107)* -- Focus your tests on the edge cases and unusual conditions where
  bugs are most likely.

<br/>

Discussions and Conclusion
============

To deepen your understanding, read the [RePatch](https://arxiv.org/pdf/2508.06718) paper and use it to guide your
answers:

* Did your test confirm that the patch works correctly in the target repository? If not, what additional
  adaptations might be needed?
* How does patch technical lag (as discussed in PaReco) affect the reliability of tests when integrating
  long-delayed patches?
* RePatch found that many cherry-pick failures stem from refactorings such as Rename Method or Rename Parameter.
  How might such refactorings influence the kinds of tests you need to write?
* How do unit and integration tests together strengthen confidence in patch reuse across software variants? Where
  might tests still fall short?
* Imagine your integrated patch passes syntactic checks and unit tests but fails in production. Based on the
  research papers, what variant-specific factors could explain this outcome?

Post-Lab Quiz: Software Integration
==========
The quiz for this session is posted on WebCampus.
