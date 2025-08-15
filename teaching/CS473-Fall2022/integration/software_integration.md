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

In this session, we will explore tools that assist in software integration across related but 
independently evolving repositories. Many software variants (forks that share a common origin) fail to 
reuse relevant bug fixes or enhancements from each other. Prior work with **PaReco**
([paper](https://dl.acm.org/doi/10.1145/3540250.3549112)) shows that reuse gaps often appear as missed 
opportunities (patch present in the source but absent in the target) or effort duplication (similar patch 
re‑implemented manually). Our extended tool, **GACPD**, builds on **PaReco** with broader language support, 
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
In this lab you will play with two very related tools: [GACPD](https://github.com/unlv-evol/GACPD) and [RePatch](https://github.com/unlv-evol/RePatch)

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

## Task 2 – Patch Integration with - RePatch
