---
layout: page
title: Reengineering Project - linkedin/kafka
permalink: /teaching/Software-Reengineering/project/
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
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Software Integration" />
</form>
<form action="/teaching/Software-Reengineering/msr/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Mining Software Repositories" />
</form>
<form action="/teaching/Software-Reengineering/project/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Reengineering Project" />
</form>

<br/>
<br/>

# Target Application

[linkedin/kafka](https://github.com/linkedin/kafka) is a variant fork of
[apache/kafka](https://github.com/apache/kafka) -- the version of Kafka that runs in production at LinkedIn.

Kafka was born at LinkedIn. They run thousands of brokers delivering trillions of messages per day, on a slightly
modified version of Apache Kafka trunk. The [linkedin/kafka](https://github.com/linkedin/kafka) repository holds
that LinkedIn Kafka release.

> **Work on the default branch, `3.0-li`.** That is LinkedIn's Kafka 3.0 line and the target variant used
> throughout the course, including Task 2 of the
> [Software Integration](/teaching/Software-Reengineering/integration/) lab. Its mainline counterpart is
> `apache/kafka`'s `trunk`.

### The project at a glance

1. **Form a group** (up to three members), fork `linkedin/kafka`, and build it -- Section 3
   and Section 4.
2. **Split your group's 21 PRs** from the
   [PR Categories Spreadsheet](https://docs.google.com/spreadsheets/d/1c2Y9p3mnBy5i_TP-7TNk2LkesAIsvoPma1MzAkU6WkA/edit?usp=sharing)
   among the members -- Section 2.
3. **Integrate each PR** into `3.0-li` with `git cherry-pick` (Categories 1-2) or RePatch (Categories 3-4), and
   test it -- Section 2 and Section 5.
4. **Write three reports** and submit each one on Canvas by its deadline:

| Deliverable | Due (11h59 pm) |
|---|---|
| **[Milestone 1]** Project definition, group assembly & Pre-conditions Report | Wed 10/07/2026 |
| **[Milestone 2]** Intermediate Report (tool usage) | Wed 11/04/2026 |
| Feedback session on the Intermediate Report | Mon 11/16/2026 |
| **[Milestone 3]** Final Report | Wed 12/02/2026 |
| Oral exam / presentation | Wed 12/09/2026 (to be confirmed) |

These dates mirror the timetable on the [course main page](/teaching/Software-Reengineering/); if the two ever
disagree, the course page wins.

<br/>

# 1. Contextualization of the Project

[linkedin/kafka](https://github.com/linkedin/kafka) is a **clone-and-own** variant of
[apache/kafka](https://github.com/apache/kafka): it was created by copying and adapting the existing Apache Kafka
code. For a while the two systems kept synchronizing their updates. Past the **divergence date** -- 2021-07-06 for
the branches we use -- they stopped sharing commits, yet both keep evolving actively and in parallel.

Development then becomes redundant and maintenance effort grows quickly. If a bug is found in a shared file and
fixed in one variant, it is no longer easy to tell whether it has been fixed in the other.

**Timeline of the divergence** -- `apache/kafka:trunk` against `linkedin/kafka:3.0-li`, measured 2026-09-28:

| Event | Date / value |
|---|---|
| Shared history begins -- Kafka's initial check-in to Apache SVN | 2011-08-01 |
| The GitHub fork `linkedin/kafka` is created | 2018-08-31 |
| **Last shared commit** -- merge base `f29c43bdbb85` | **2021-07-06** |
| Commits in `linkedin/kafka` that are not in `apache/kafka` | 475 |
| Commits in `apache/kafka` that are not in `linkedin/kafka` | 9,145 |

You can reproduce every figure above with the GitHub compare API -- a technique from the
[Mining Software Repositories](/teaching/Software-Reengineering/msr/) lab:

```
https://api.github.com/repos/linkedin/kafka/compare/apache:trunk...linkedin:3.0-li
```

Note how lopsided the divergence is: the mainline has moved on by more than nine thousand commits. Every one of
them is a potential fix the fork never received.

> **Be careful with commit dates.** Nearly every LinkedIn commit on `3.0-li` carries the committer date
> `2022-06-02T17:08:46Z`, while the author dates of those same commits are spread over the preceding months.
> LinkedIn rebased the branch, and the rebase re-stamped every commit. A script that reads *committer* dates will
> therefore report the divergence as 2022-06-02, which is an artifact of rewritten history, not a real event. The
> true last shared commit is the merge base in the table: 2021-07-06. When you mine this history, prefer **author**
> dates -- and remember that it is the **merge base**, not any timestamp, that decides whether a cherry-pick
> conflicts.

LinkedIn maintains several release lines, and each one left the mainline at a different point:

| LinkedIn line | Diverged from `apache/kafka:trunk` |
|---|---|
| `2.4-li` | 2019-10-07 |
| **`3.0-li`** (used in this course) | **2021-07-06** |
| `3.6-li` | 2023-08-20 |
| `3.9-li` | 2024-07-29 |

Note also that `linkedin/kafka`'s own `trunk` branch is only a mirror of the mainline -- it carries no
LinkedIn-specific commits, so it is not the variant you want. Always work from **`3.0-li`**.

### The clone-and-own problem

The figure below illustrates the **clone-and-own** development model, in which the **Target Variant** (the forked
repository) was cloned from the **Source Variant** (the original repository) and then maintained independently.

When the Target Variant was forked (**fork_date**), it inherited all commits from the Source Variant. Between the
**fork_date** and the **divergence_date**, both variants continued synchronizing commits, keeping their histories
aligned. After the **divergence_date**, synchronization stopped and the two variants began to evolve
independently.

<div style="text-align: center;">
<img src="/images/problem.jpeg" alt="Clone-and-own divergence between a source and a target variant" style="width:100%;max-width:1000px;" />
</div>

Now assume that, after the **divergence_date**, a developer on the **Source Variant** finds a bug in `Foo.java`.
They create a bugfix branch, apply the patch, and merge the fix into the main branch of the Source Variant through
a pull request.

Later, the maintainer of the **Target Variant** wants that same fix in the `git_head` of their repository. Two
things can happen:

1. **Successful integration.** The commit applies cleanly. The patch merges without conflicts and the fixed
   `Foo.java` becomes part of the target's codebase.
2. **Failed integration.** The commit fails to apply because of **merge conflicts** in `Foo.java`, arising from
   code divergence, refactoring, or other structural differences accumulated since the **divergence_date**.

Because the fork has diverged, files shared by a patch may have changed in both variants, so a direct
`git cherry-pick` often conflicts. Some of those conflicts are purely **textual** -- overlapping edits on the same
lines. Others are **structural**, caused by **refactorings** applied independently in each variant: method
renames, class moves, changed interfaces.

### The tool: RePatch

This project uses **[RePatch](https://github.com/Software-Reengineering/RePatch/tree/RePatch-2.0-upgrade)** (the
**`RePatch-2.0-upgrade`** branch), which performs **refactoring-aware patch integration**: it aligns the source
and target around the refactorings it detects, applies the patch, then replays those refactorings so the target
keeps its own structure.

You have already run RePatch in **Task 2 of the
[Software Integration](/teaching/Software-Reengineering/integration/) lab**, on PR #13386. For the project:

* **Reuse that workflow.** The lab's headless path is the quickest route -- `repatch <label> <source> <target> <pr>`
  for a single PR, or a CSV batch for several at once. The lab also covers the IDE route and where to read results.
* **Inspect the results** in the RePatch database -- `merge_result`, `conflicting_file`, `conflict_block`,
  `refactoring`, `refactoring_conflict` -- and document how each conflict was resolved, or why it could not be.
* **Connect your observations** back to the reengineering patterns in the OORP book.

> RePatch is needed only for **Categories 3 and 4** below -- **four PRs in total**, the same four the integration
> lab refers to. Categories 1 and 2 are handled with plain `git cherry-pick`.

<br/>

# 2. Pull Request Categories

You will work on pull requests from the four categories described below. The specific PRs are listed in the
[PR Categories Spreadsheet](https://docs.google.com/spreadsheets/d/1c2Y9p3mnBy5i_TP-7TNk2LkesAIsvoPma1MzAkU6WkA/edit?usp=sharing).

Each **group** is assigned **21 PRs**, which works out to seven per student in a group of three:

| Category | PRs per group | Per student | Integration route |
|---|---|---|---|
| 1 -- cherry-pick succeeds, tests exist | 3 | 1 | `git cherry-pick` |
| 2 -- cherry-pick succeeds, tests missing | 6 | 2 | `git cherry-pick` + new tests |
| 3 -- cherry-pick fails, RePatch succeeds | 3 | 1 | RePatch |
| 4 -- cherry-pick fails, RePatch fails | 9 | 3 | RePatch + manual analysis |
| **Total** | **21** | **7** | |

**How you divide these PRs among yourselves is up to your group.** Decide early, and write the split down -- the
report has to show it. Keep the category mix balanced across members: nobody should end up owning only Category 4
work, since those PRs cannot be integrated and are the least satisfying to carry alone.

> **Check the `Replacement` column.** For some Category 1 and 2 PRs the originally selected pull request turned
> out to conflict, so a **replacement PR** is listed beside it. Where a replacement is given, work on the
> **replacement**, not the original.

This is a group project, so you are expected to **collaborate** rather than work in parallel silos:

* Discuss your findings, challenges, and approaches together.
* Share insights on conflicts, testing, and coverage -- the same refactoring often blocks several PRs.
* Submit one **joint team report** consolidating everyone's contributions.
* Include a short **contribution table** naming which PRs each member handled, so individual work stays
  identifiable.

### Category 1: Cherry-pick succeeds and tests already exist

* `git cherry-pick` succeeds without conflicts.
* The integrated code is already covered by tests in the target repository.

**Tasks:**

* Identify the **merge commit** of the pull request, using the techniques from the
  [Mining Software Repositories](/teaching/Software-Reengineering/msr/) lab.
* Run `git cherry-pick` on that merge commit.
* Validate the integration by running the existing test suite.

### Category 2: Cherry-pick succeeds but tests are missing

* `git cherry-pick` succeeds without conflicts.
* Some of the changed files lack tests in the target repository.

**Tasks:**

* Identify the **merge commit** of the pull request.
* Run `git cherry-pick` on that merge commit.
* Write the missing unit or integration tests for the uncovered changes.
* Measure coverage **before and after** adding the tests, to show the improvement. See
  [Appendix A](#appendix-a-measuring-coverage-on-linkedinkafka) for the commands and for the PowerMock caveat.

### Category 3: Cherry-pick fails, RePatch succeeds

* `git cherry-pick` fails because of structural divergence.
* RePatch resolves the conflicts and integrates the PR.
* The affected files may or may not have test coverage.

**Tasks:**

* Run RePatch and inspect the integration results to confirm correctness.
* Validate the integration by running the existing test suite.
* If tests are missing, write unit or integration tests for the uncovered changes.
* Measure coverage **before and after** adding tests -- see
  [Appendix A](#appendix-a-measuring-coverage-on-linkedinkafka).

### Category 4: Cherry-pick fails, RePatch cannot resolve the conflicts

* Both `git cherry-pick` and RePatch fail, because of **unsupported refactorings** or **complex semantic or
  textual conflicts**.

**Tasks:**

* Identify and document the specific reason for the failure -- an unsupported refactoring, a semantic conflict, or
  another complex change.
* Attempt small, targeted manual adaptations, for example updating a method signature or supplying a missing
  parameter.
* If integration remains infeasible, explain clearly why developer intervention and domain knowledge are required.
* Reflect on the nature of these conflicts and suggest directions for extending or improving **RePatch** to handle
  them.

<br/>

# 3. Pre-conditions Report

Each group submits a **Pre-conditions Report (PDF)**. Only **one member per group** uploads it on Canvas on behalf
of the team. Groups have a **maximum of three members**; groups of one or two are also allowed.

This and the later reports are graded against the checklists on the
[course main page](/teaching/Software-Reengineering/):
[Pre-conditions](../../../files/CS789_SRE/Pre-conditions_Report_Evaluation_Template.pdf) &middot;
[Intermediate](../../../files/CS789_SRE/Intermetdiate_Evaluation_Report_Template.pdf) &middot;
[Final](../../../files/CS789_SRE/Final_Evaluation_Report_CS-789_Template.pdf). Read the relevant checklist
*before* you write the report. All deadlines are in the table under
[The project at a glance](#the-project-at-a-glance).

The Pre-conditions Report must contain the four parts below.

### 3.1 Group and repository setup

* Project name.
* Full names of all group members.
* A link to your **fork of [linkedin/kafka](https://github.com/linkedin/kafka)**.
* Confirmation that all group members are added as collaborators on the fork.
* Add the instructor as a collaborator as well -- GitHub ID [`johnxu21`](https://github.com/johnxu21).

### 3.2 Build confirmation

* A short statement confirming that your group **built the project successfully**.
* Each group member includes a **screenshot from their own IDE** showing the project source and a
  *"Build successful"* (or equivalent) message.
* Compile all screenshots into the same PDF report.

### 3.3 Initial system understanding

Provide a **simple class diagram** for one of the pull requests you will work on (or for the buggy target). This
reinforces your **Initial Understanding** (OORP, p.83) of the system. Include only:

* the class(es) affected by the patch, and
* the classes those classes call directly.

Do **not** include transitive dependencies: if class A calls class B and class B calls class C, you do not need
class C. A simple class diagram carries only class names and their interactions. Strict UML notation is **not**
required -- clarity of the interactions is what matters. See the examples in the
[JPacman repository's `doc/uml` folder](https://github.com/johnxu21/jpacman/blob/master/doc/uml/FactoryWiring.png).

### 3.4 Planning of scope and goals (optional)

This section is optional, but it appears on the evaluation form, and the items it asks for come back as *graded*
criteria in the Intermediate and Final reports -- so writing them down now costs little and pays off later:

* **Meeting schedule** -- how often, and online or in person?
* **Communication schedule** -- which tools, and how quickly are messages expected to be answered (Discord,
  Slack, email, GitHub issues)?
* **Collaboration practices** -- how will you share progress on your PRs (status updates, peer reviews, joint
  testing sessions)?
* **Ad-hoc or systematic?** -- state which approach your group is taking. You will be asked to reflect on this
  choice in both later reports.
* **Timeline and milestones** -- when will you finish Categories 1-4, draft the reports, and run reviews?
* **Success criteria** -- your "definition of done" for a PR. When is a Category 2 PR finished? When is a
  Category 4 PR adequately explained?
* **Contingency plan** -- how will you handle missed deadlines, unresolved conflicts, or an unavailable teammate?

<br/>

# 4. General Coding Instructions

When working on this assignment, follow these repository and coding practices.

**Fork and clone**

* Fork [linkedin/kafka](https://github.com/linkedin/kafka) and clone it for your team to work on.
* Refer to the project's own documentation for build instructions, but adapt as needed -- open-source
  documentation is often out of date.
* Build with **JDK 11**, not JDK 17 -- see [Appendix A.2](#a2-build-the-clone-with-jdk-11). In IntelliJ, set
  both the Project SDK and the Gradle JVM to 11.

```bash
git clone https://github.com/<your-group>/kafka.git
cd kafka
git checkout 3.0-li
export JAVA_HOME=/usr/lib/jvm/java-11        # adjust to your system
./gradlew jar                                 # compiles everything; takes a while the first time
```

**Cherry-picking a mainline PR (Categories 1 and 2)**

Your fork contains only LinkedIn's history, so the Apache commit you want to cherry-pick is not in it yet. Add
`apache/kafka` as a second remote once, then work on **one branch per PR** so that each integration can be
reviewed and graded on its own:

```bash
git remote add upstream https://github.com/apache/kafka.git     # once per clone
git fetch upstream trunk

# find the commit that merged the PR -- the "merge_commit_sha" field
curl -s https://api.github.com/repos/apache/kafka/pulls/<PR> | grep merge_commit_sha

git checkout -b pr-<PR> 3.0-li
git cherry-pick <merge_commit_sha>
git push origin pr-<PR>
```

`apache/kafka` squash-merges its pull requests, so `merge_commit_sha` is an ordinary single-parent commit and
`git cherry-pick` needs no `-m` option. If the cherry-pick unexpectedly conflicts on a Category 1 or 2 PR, run
`git cherry-pick --abort`, check the `Replacement` column of the spreadsheet, and tell the instructor if the
problem remains.

**Collaboration**

* Add all members as collaborators on the fork.
* Make sure everyone can build, test, and push changes.

**Commit and push practices**

* Commit and push **regularly**, with clear, descriptive messages.
* Each commit should represent a **single coherent activity** -- resolving a conflict, adding tests, applying a
  patch.
* Avoid large commits that combine unrelated changes.
* Where possible, separate code changes from test changes; it improves traceability.

**Commit message guidelines**

Write concise messages that explain the purpose of the change, for example:

```
fixing merge conflicts on patch X, class Y
adding unit tests for class Y
refactoring class Y to apply patch + added new test
```

**Commit history and evaluation**

* Your GitHub commit history is reviewed as part of the evaluation: a consistent, clear, incremental history is
  expected.
* Commit and push the **final version** of your project before the deadline.

<br/>

# 5. Development Activities

For each assigned pull request, perform the following activities and document them in your project report.

### I. Design recovery

<div style="text-align: center;">
<img src="/images/473/design_recovery.jpeg" alt="Design recovery" style="width:100%;max-width:500px;" />
</div>

* Extract and describe the **local design** of the classes and methods affected by the pull request in the
  **source variant**, using IntelliJ or a similar tool.
* Identify the **corresponding classes or components** in the **target variant**, where the integration will
  happen.
* Compare both contexts to highlight structural or architectural differences: renamed classes, relocated methods,
  split responsibilities.
* A side-by-side diagram or annotated class sketch is enough; the goal is to show the **design gap** between the
  two variants.
* **For Category 4 PRs:** analyze the existing design of the target variant and identify the architectural
  misalignments or refactoring-induced differences that prevent integration. Since the patch cannot be
  integrated, no redesign is expected -- only a discussion of the design barriers.

### II. Design adaptation / redesign

<div style="text-align: center;">
<img src="/images/473/Redesign.jpeg" alt="Redesign" style="width:100%;max-width:450px;" />
</div>

* Analyze how the integrated patch modifies or extends the existing design.
* Compose a **revised design view** showing how the functionality now fits into the system and interacts with
  related components.
* If you wrote new tests, explain how the design of the test suite evolved to accommodate the change.
* Confirm that the redesign supports the fix or feature without degrading code quality.
* **For Category 4 PRs:** no revised design is expected, since those PRs fail to integrate. Describe instead the
  **design barriers** that caused the failure -- incompatible refactorings, a missing interface, a semantic
  mismatch.

### III. Integration and testing

* Attempt the integration with `git cherry-pick`.
* If cherry-pick fails, run **RePatch** and document the results.
* Validate the integration by running the target variant's test suite.
* If tests are missing, write appropriate unit or integration tests.
* Report **coverage before and after** integration, and reflect on the adequacy of the test suite.
  [Appendix A](#appendix-a-measuring-coverage-on-linkedinkafka) explains how to measure it on this build.

### IV. Project management

<div style="text-align: center;">
<img src="/images/473/project-management.jpeg" alt="Project management" style="width:100%;max-width:550px;" />
</div>

* Estimate the effort required for (i) integrating the patch and (ii) creating or adapting tests.
* Identify PRs that were **exceptional entities** -- a large number of changed files, unusually complex conflicts.
* Comment on risks to maintainability and on long-term design debt introduced by the integration.

### V. Refactoring and manual resolution

<div style="text-align: center;">
<img src="/images/473/refactor1.jpeg" alt="Refactoring and manual resolution" style="width:100%;max-width:400px;" />
</div>

* If RePatch cannot resolve the conflicts, attempt **manual resolution** -- adjusting parameters, handling renamed
  methods.
* Document any **refactorings** you performed to make the integration feasible.
* If manual resolution is not possible without knowing developer intent, explain why.
* Make sure the tests remain effective and coverage is preserved after your changes.

### VI. Reflection on patterns, techniques, and teamwork

* Identify the **reengineering patterns** from the OORP book that informed your design, integration, testing, and
  refactoring decisions.
* Reflect on how your team coordinated across the four categories (meetings, reviews, shared testing).
* Summarize what you learned about **design, variant-aware integration, and testing**.

Your report should also demonstrate the techniques introduced in the lab sessions:

* **Analyzing** -- Metrics & Visualization; Mining Software Repositories.
* **Restructuring** -- Testing, Refactoring, and Integration.

The Intermediate Report is graded on using **at least one tool or script from each lab session**:

| Lab session | Tools you can use |
|---|---|
| Metrics & Visualization | CodeScene |
| Refactoring Assistants | CodeScene, SonarQube, RefactoringMiner |
| Dynamic Analysis: Testing | IntelliJ Coverage, JaCoCo |
| Software Integration | GACPD, RePatch |
| Mining Software Repositories | GitHub REST API, GraphQL |

Within each row you may pick whichever tool suits you, and you may add tools not covered in the labs -- but you
must **justify your choices**: explain why you applied a given technique, why others were not relevant, and what
the benefits and drawbacks turned out to be.

**Testing requirements**

* Determine how well the existing tests give you feedback during refactoring and integration.
* **Quantify adequacy** -- show coverage before and after (see
  [Appendix A](#appendix-a-measuring-coverage-on-linkedinkafka)); where a metric is invalidated by the build,
  say so and argue adequacy another way.
* Argue whether the tests are sufficient for your scenario.
* If they are inadequate, extend them efficiently: balance thoroughness against time invested.

<br/>

# 6. General Evaluation

Your Final Report is graded against the
[Final Report checklist](../../../files/CS789_SRE/Final_Evaluation_Report_CS-789_Template.pdf). The headings below
follow that checklist, so you can use it as a self-assessment before you submit.

**Delivery**

* The report is submitted on Canvas by the deadline. Late submissions are recorded.

**Coverage of the PR categories**

* All **four** categories are documented -- including Category 4, where the outcome is an explanation of why
  integration failed rather than integrated code.

**Design recovery and adaptation**

* Class diagrams are provided for the affected PRs.
* The current design is described clearly.
* The revised design, and the integration's impact on the architecture, is explained.

**Integration and refactoring activities**

* The integration process is described -- cherry-pick, RePatch, manual fixes.
* The refactorings you applied are justified and documented.
* You provide evidence that your restructurings are **behavior-preserving**: successful compilation, passing
  tests, and coverage maintained or improved.

**Testing and coverage**

* You confirm whether the existing tests actually cover the integrated PRs.
* New tests are written where they were missing.
* Coverage **before and after** is reported, with outputs or screenshots.
* The adequacy of the test suite is discussed, not just its percentage.

**Use of tools and techniques**

* Tools from the labs are applied -- metrics, visualization, mining, coverage, integration, refactoring.
* Outputs or screenshots are included for the relevant tools.
* You reflect on how effective each tool actually was for this project.
* Any extra tools beyond the labs are described.

**Reengineering patterns**

* Patterns are applied **in context** -- design, integration, testing, refactoring -- not listed in isolation.
* Your choice of patterns is justified.
* You reflect on which patterns proved most useful.

**Effort and risk assessment**

* Effort estimates are documented, for both integration and testing.
* Exceptional PRs are identified -- large, or conflict-heavy.
* Risks to maintainability and correctness are discussed.

**Teamwork and coordination**

* Team coordination is described: meetings, communication tools, peer reviews.
* You identify whether your approach was **ad-hoc or systematic**, and reflect on it.
* Your **success criteria** ("definition of done") are addressed.
* Your timeline and milestones are shown as followed, or adapted with an explanation.

**Report quality**

* Structure is logical and follows the project categories and activities.
* Layout is clear, readable, and professional.
* Spelling and grammar are acceptable.
* Evidence -- screenshots, diagrams, logs -- is included where relevant.
* Reasoning is explained: decisions, not just results.

**Overall**

* The report presents a sound, systematic reengineering process.
* It demonstrates lessons learned about variant-aware reengineering.
* It is good enough to serve as a reference for future projects.

<br/>

# 7. Report

This project is a **software reengineering process** applied to variant-aware patch integration. Your report
should show how you applied reengineering concepts -- analysis, design recovery, restructuring, and validation --
across the four PR categories.

Address the following.

**Context**

* Briefly describe your project's context: reengineering through patch integration across diverged variants
  (`apache/kafka` to `linkedin/kafka`).
* Frame it as a reengineering challenge, not merely a code merge.

**Problem at hand**

* Clarify the reengineering problems you met during PR integration -- divergence, refactoring conflicts, missing
  tests.
* Discuss their intrinsic difficulties.

**Reengineering patterns**

You must show how OORP patterns guided your work. Do **not** list patterns in isolation; introduce each one in the
context where you applied it:

* **Design recovery / adaptation** -- which patterns helped you understand or adapt the architecture?
* **Integration** -- which patterns helped you resolve conflicts or prioritize patches?
* **Testing** -- which patterns informed how you verified correctness or extended the suite?
* **Refactoring** -- which patterns guided structural changes while preserving behavior?

In your reflection section, summarize briefly which patterns proved most useful across the categories, and why.

**Teamwork and coordination**

* Describe how your team coordinated work across the four categories.
* Explain how responsibilities were assigned, how reviews were conducted, and how challenges were addressed.
* Reflect on how effective your coordination strategy was.

**Reflection on techniques**

* Discuss which analysis techniques from the labs you applied -- metrics, mining, visualization, integration
  tools, testing.
* Justify your choices and evaluate their benefits and drawbacks.
* Consider alternative techniques or tools where relevant.

**Conclusion**

* Summarize what you learned about **software reengineering in the context of PR integration**.
* Highlight insights about design, testing, refactoring, and teamwork that generalize beyond this case.

> **Scope of each report.** The **Pre-conditions Report** only establishes setup, though early planning on
> patterns and risks will strengthen your final outcome. The **Intermediate Report** covers work in progress, so
> partial results are expected -- but it is graded on its own checklist, which asks for a tool from *every* lab
> session, screenshots of their output, UML diagrams of the structural changes you are planning, and evidence
> comparing the system **before, during and after** reengineering. The **Final Report** gives a full, polished
> account of the whole process. Read each checklist before you start writing.

<br/>

# 8. LLM-Assisted Integration and Test Generation

Category 4 is where the automation runs out. `git cherry-pick` fails, RePatch cannot invert the refactorings, and
[Section 2](#category-4-cherry-pick-fails-repatch-cannot-resolve-the-conflicts) asks you to explain why developer
intervention is required. This bonus asks a narrower question:

> **How far can a small language model, running on your own machine, close that gap?**

This is a genuine open question, not an exercise with a known answer. A careful negative result -- "we tried, here
is exactly where and how it failed" -- earns full bonus credit. An uncritical "the LLM fixed it" with no
verification earns none.

The bonus has two parts. **Part A** applies the model to integration, **Part B** to testing. You may attempt one
or both. The weight of the bonus is announced on Canvas.

### Ground rules

These apply to everything below, and they are what separates a result from an anecdote.

* **Local models only.** The point is to see what runs on ordinary hardware, without sending a company's source
  code to a third party. No hosted APIs.
* **Everything must be verified.** Generated code counts only if it **compiles** and you have **run the tests**.
  Nothing is accepted on the model's say-so.
* **Everything must be reproducible.** Record the exact model and tag, the full prompts, the sampling settings,
  and the raw output -- including the attempts that failed. Commit them to your fork under `llm-bonus/`.
* **Report honestly.** Hallucinated APIs, invented method names, and confidently wrong patches are findings.
  Write them down; they are the most interesting part of the result.
* **Disclose it.** Say in the report which parts of your submission were produced with model assistance.
* **Do not push generated code upstream.** Your fork only -- never a pull request to `apache/kafka` or
  `linkedin/kafka`.

### 8.1 Set up a local model

[Ollama](https://ollama.com) is the simplest runner. Install it on your **host machine**, not inside the RePatch
container -- that container already claims about 10 GB of RAM, and the two will fight over memory.

```bash
ollama pull qwen2.5-coder:7b
ollama run qwen2.5-coder:7b            # interactive check that it works
ollama show qwen2.5-coder:7b           # record this output: tag, digest, parameters
```

Pick the largest model your machine can hold:

| Model | Download | Practical on |
|---|---|---|
| `qwen2.5-coder:3b` | 1.9 GB | 8 GB RAM, no GPU |
| **`qwen2.5-coder:7b`** | 4.7 GB | 16 GB RAM -- the default choice |
| `qwen2.5-coder:14b` | 9.0 GB | 32 GB RAM, or a 12 GB+ GPU |

Other code-oriented families work too (`deepseek-coder-v2`, `codellama`, `llama3.1`). If you compare two models,
say so -- that is a result in itself.

Set **`temperature 0`** for every run in this bonus. You are trying to produce something another group could
reproduce, not something creative.

### 8.2 Part A -- LLM-assisted patch integration

Pick **one** of your group's Category 4 PRs. One, done carefully, is worth far more than nine done loosely.

**1. Establish the baseline.** Before involving the model, record what already failed: the `git cherry-pick`
error, RePatch's outcome, and which refactorings RePatch detected but could not invert (`repatch log`, and the
`refactoring` and `refactoring_conflict` tables). You cannot claim the model helped without knowing precisely
what it is being compared against.

**2. Budget your context.** A 7B model has roughly a 32K-token window, and Kafka's files are large --
`WorkerSourceTask.java` alone would consume much of it. You cannot paste whole files. Assemble the smallest
prompt that could possibly work:

* the **mainline hunk** from the source PR (this is your ground truth for *intent*);
* the **corresponding method** in the target variant, as it actually exists;
* the signatures of the types involved -- not their bodies;
* one sentence on how the two variants diverged here.

Deciding what to include *is* the exercise. It is **Refactor to Understand** (OORP, p.127) done by hand: you
cannot select the relevant context until you understand the change.

**3. A starting prompt.** Adapt it; do not treat it as fixed.

```text
You are adapting a patch between two diverged forks of Apache Kafka.

SOURCE (apache/kafka) -- the change to be ported:
<the diff hunk>

TARGET (linkedin/kafka 3.0-li) -- the code as it exists today:
<the corresponding method, verbatim>

The target diverged from the source at commit f29c43bdbb85 (2021-07-06).
In this area the variants differ as follows: <your one-sentence description>.

Produce the edited target method so that it carries the same behavioral change
as the source hunk. Preserve the target's existing names, types and style.
Output only the Java code. If the change cannot be applied safely, say so and
explain which fact you would need to know.
```

That last instruction matters: a model that is allowed to decline will sometimes tell you what is missing, which
is more useful than a fabricated patch.

**4. Iterate against the compiler.** Apply the output, compile the module, and feed the errors back into the next
prompt. Record how many rounds you needed and whether it converged or oscillated.

```bash
export JAVA_HOME=/usr/lib/jvm/java-11
./gradlew :connect:runtime:compileJava      # substitute your module
```

**5. Verify.** In this order:

* Does it **compile**?
* Do the module's **existing tests** still pass?
* Does the patch actually carry the **mainline change's intent** -- not merely something that compiles? Compare
  against the source PR yourself.
* Did the model handle the specific refactoring that defeated RePatch, or did it sidestep it by rewriting
  something else?

**6. Report.** Include the baseline, the prompts, the number of iterations, the final diff, the verification
results, and your judgement: did this produce an integration a maintainer could accept, a plausible-looking patch
that does the wrong thing, or nothing usable?

### 8.3 Part B -- Regression check, then test generation

Take **one PR you actually integrated** (Category 1, 2 or 3, or a Part A success). Do the two steps in this order;
the order is the point.

**Step 1 -- check for regressions first.**

Integration can break tests that used to pass. Find out before you write anything new:

```bash
export JAVA_HOME=/usr/lib/jvm/java-11
./gradlew :connect:runtime:test          # the module you touched
```

Compare against the same module's results **before** integration. Any test that passed before and fails now is a
regression caused by your integration -- diagnose it and say whether it indicates a genuine behavioral conflict
or merely a test that encoded the target's old structure. This is **Tests: Your Life Insurance** (OORP, p.149)
being cashed in: the suite's whole purpose is to tell you this.

Do not proceed to Step 2 until the suite is green, or until you can explain every failure.

**Step 2 -- generate tests to raise coverage.**

Measure coverage first, following [Appendix A](#appendix-a-measuring-coverage-on-linkedinkafka), so you know which
lines and branches of the integrated change are unexercised. Then ask the model for tests targeting exactly those.

Give it the method under test, an **existing test from the same class as a style example**, and the specific
branch you want covered. The style example matters here more than anywhere else: `3.0-li` is **JUnit 4 with
EasyMock and PowerMock**, while most Java test code a model has seen is JUnit 5 with Mockito. Without an example
it will confidently generate tests in the wrong framework that do not compile.

**Then validate what it produced.** Generated tests are guilty until proven innocent:

* Does the test **compile** and pass?
* **Can it fail?** Revert the integrated change, re-run the test, and confirm it now fails. A test that passes in
  both states asserts nothing. This is the same check you applied in Task 3 of the
  [Software Integration](/teaching/Software-Reengineering/integration/) lab, and generated tests fail it often --
  a common failure mode is a test that asserts only that no exception was thrown.
* Does it test **behavior**, or does it restate the implementation line by line?
* Re-measure coverage. Did it move? Remember the PowerMock caveat in
  [Appendix A](#appendix-a-measuring-coverage-on-linkedinkafka): if the class is PowerMock-mocked, coverage may
  read 0% however good the test is. Report that rather than discarding the test.

Keep the tests that survive. Delete the rest, and say how many you discarded and why -- the **ratio of generated
tests to usable tests** is one of the most informative numbers you can report.

### 8.4 What to hand in

Add a clearly marked bonus section to your Final Report containing:

* the model, tag and digest (`ollama show`), your sampling settings, and your hardware;
* every prompt, and the raw outputs, committed under `llm-bonus/` in your fork;
* **Part A:** the baseline failure, the final diff, iteration count, and verification results;
* **Part B:** the regression results before and after integration, the generated tests you kept and discarded
  with the reason, and coverage before and after;
* an honest assessment: where the model helped, where it wasted your time, and where it was confidently wrong.

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **Tests: Your Life Insurance** *(p.149)* -- The regression check in Step 1 is exactly what the suite exists for.
  A generated patch you have not tested is not an integration.
- **Write Tests to Understand** *(p.179)* -- If you cannot tell whether a generated test is meaningful, you do not
  yet understand the code well enough to accept the generated patch either.
- **Grow Your Test Base Incrementally** *(p.159)* -- Add the surviving tests a few at a time, checking each one,
  rather than committing everything the model emitted.
- **Refactor to Understand** *(p.127)* -- Selecting the minimal context for the prompt forces the same
  understanding that a manual integration would have required.
- **Keep It Simple** *(p.37)* -- One PR, examined properly, beats nine generated patches nobody verified.

<br/>

# 9. Final Remarks

If you have any questions about the project or the report, please get in touch with the instructor or the TAs.

<br/>

# Appendix A. Measuring Coverage on linkedin/kafka

Categories 2 and 3 ask you to report coverage **before and after** adding tests, and the
[Final Report checklist](../../../files/CS789_SRE/Final_Evaluation_Report_CS-789_Template.pdf) grades it. The
coverage lab used Coverage.py on a small Python project; `linkedin/kafka` is a large Java and Scala build, so the
mechanics are different. This appendix gives you the working commands and the one trap you are likely to hit.

### A.1 Coverage is switched off by default

The build only applies its coverage plugins when you ask for them (`build.gradle`, line 133):

```groovy
userEnableTestCoverage = project.hasProperty("enableTestCoverage") ? enableTestCoverage : false
```

So every coverage command below needs **`-PenableTestCoverage`**. Without it the coverage tasks do not exist, and
Gradle fails with "task not found" rather than with anything that explains why.

### A.2 Build the clone with JDK 11

`3.0-li` ships the Gradle 7.1.1 wrapper, which predates JDK 17 support. Use **JDK 11** for anything you run inside
the kafka clone:

```bash
export JAVA_HOME=/usr/lib/jvm/java-11        # path as provided by your container or system
./gradlew -version                            # confirm before going further
```

JDK 17 is what builds *RePatch*. The kafka clone is a different toolchain -- do not mix them up.

### A.3 Scope the run to one module

Two tasks are named `reportCoverage`, and the difference matters:

| Task | What it does |
|---|---|
| `:connect:runtime:reportCoverage` | Tests and reports **one module**. Use this. |
| `reportCoverage` (root) | `jacocoRootReport` + `core:reportCoverage` -- runs **every test in Kafka**. Hours. Avoid. |

For a module, `jacocoTestReport` already depends on `test`, so one task does both:

```bash
./gradlew -PenableTestCoverage :connect:runtime:reportCoverage
```

To scope further to a single test class, name the `test` task so the `--tests` filter binds to it, then ask for
the report:

```bash
./gradlew -PenableTestCoverage \
  :connect:runtime:test --tests "org.apache.kafka.connect.runtime.WorkerSourceTaskTest" \
  :connect:runtime:jacocoTestReport
```

Substitute the module your PR touches. If you are not sure which module a file belongs to, its path tells you:
`connect/runtime/src/main/java/...` is `:connect:runtime`.

### A.4 Where the reports land

* **Java modules (JaCoCo 0.8.7)** -- HTML and XML under `<module>/build/reports/jacoco/`, for example
  `connect/runtime/build/reports/jacoco/`. Open `index.html` in the HTML directory.
* **`:core` (Scala)** -- `:core` is excluded from JaCoCo and uses **Scoverage 1.4.11** instead. Its report is
  written to `build/scoverage/` at the repository root, and the task is `:core:reportCoverage`.

Keep the *before* report before you overwrite it: copy the HTML directory aside, or save the XML, so you have both
numbers when you write the report.

### A.5 The PowerMock trap

This is the part that catches people out. The build file says so itself (line 711):

> NOTE: Jacoco Gradle plugin does not support "offline instrumentation" this means that classes mocked by
> PowerMock may report 0 coverage, since the source was modified after initial instrumentation.
> See <https://github.com/jacoco/jacoco/issues/51>

`3.0-li` is a JUnit 4 + EasyMock/PowerMock codebase, so **a class mocked by PowerMock can report 0% coverage no
matter how thoroughly you test it.** `WorkerSourceTaskTest` -- the class from Task 3 of the
[Software Integration](/teaching/Software-Reengineering/integration/) lab -- is one such test.

If you hit this, **do not** invent numbers, and do not conclude that your tests are worthless. Report it:

* state which classes reported 0% and that they are PowerMock-mocked;
* cite the limitation above as the cause;
* argue test adequacy another way -- which behaviors your new tests exercise, which branches they reach, and what
  would have to break for them to fail.

That argument is worth more than a percentage. Recognizing that a metric has been invalidated by the way the code
under test is built is itself a reengineering result, and the
[Final Report checklist](../../../files/CS789_SRE/Final_Evaluation_Report_CS-789_Template.pdf) asks you to discuss
the **adequacy** of the test suite, not merely to quote a number.

### A.6 A workable before/after routine

1. Check out the target at the state **before** your integration.
2. Run the scoped coverage command for the module your PR touches; save the report.
3. Apply the patch (cherry-pick or RePatch) and add your tests.
4. Re-run the same command, on the same module and the same scope.
5. Compare like with like, and say in the report exactly which command you ran. A coverage number without its
   scope is not interpretable -- one module's figure and the whole build's figure are not comparable.
