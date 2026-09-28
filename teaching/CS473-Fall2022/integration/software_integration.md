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
* write the missing test for that patch, and adapt it to the target variant's diverging test infrastructure.

Materials & Tools Used for this Session
========

**Slides**

* [Software Integration (PDF)](../../../files/Integration.pdf)

**IDEs**

* [PyCharm](https://www.jetbrains.com/pycharm/) -- used to run MOVis.
* [IntelliJ IDEA](https://www.jetbrains.com/idea/) -- needed only if you run RePatch through the IDE (Task 2,
  paths B and C); RePatch is an IntelliJ plugin. The Community Edition is sufficient -- the build pins the
  IntelliJ Platform to 2024.3.7 and Gradle downloads it for you. The **Ultimate Edition** adds built-in UML
  diagram generation, which you may find useful for the project report.
  Both are free for students through the [JetBrains Student Pack](https://www.jetbrains.com/academy/student-pack/).

**Repositories**

* Source repository (mainline): [apache/kafka](https://github.com/apache/kafka)
* Target repository (divergent fork): [linkedin/kafka](https://github.com/linkedin/kafka)

**Tools**

* [MOVis](https://github.com/unlv-evol/MOVis) -- front-end for GACPD; detects candidate patches for reuse.
* [RePatch](https://github.com/Software-Reengineering/RePatch/tree/RePatch-2.0-upgrade) -- refactoring-aware
  patch integration. Use the **`RePatch-2.0-upgrade`** branch. It builds on **Java 17** and ships two Docker
  images: a **headless** one with a `repatch` CLI (recommended for this lab) and a GUI dev container with
  IntelliJ preloaded. Both bundle every dependency, including MySQL.
* [Docker](https://docs.docker.com/get-started/get-docker/) -- needed for either containerized RePatch setup.

**Book**

* [Object-Oriented Reengineering Patterns](http://scg.unibe.ch/download/oorp/) (OORP)
  (_Note: OORP, p.xx refers to a page in the pdf version of this book_)

<br/>

Setup / Preparation
===============

In this lab you will work with two closely related tools:
[MOVis](https://github.com/unlv-evol/MOVis) and
[RePatch](https://github.com/Software-Reengineering/RePatch/tree/RePatch-2.0-upgrade) (the
**`RePatch-2.0-upgrade`** branch). Install each one by following its README; the per-task instructions below tell
you when you need it. **Start the RePatch setup early** -- it is the heaviest install in this course, and Task 2
explains why.

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

1. **Set up RePatch.**
2. **Run RePatch** to integrate the patch.
3. **Verify the result** by inspecting the results database.

We use the **RePatch 2.0** codebase on the
[`RePatch-2.0-upgrade`](https://github.com/Software-Reengineering/RePatch/tree/RePatch-2.0-upgrade) branch. Read
that branch's README before you start; the steps below summarize it and tell you where the lab differs.

> **Plan ahead.** RePatch is the heaviest tool in this course: budget roughly **20 GB of free disk** and **10 GB of
> RAM available to Docker**, plus a one-time image build or dependency download of around ten minutes. RePatch 2.0
> builds and runs on **Java 17**. Do not leave this task to the last evening.

### 1. Set up RePatch

Pick **one** of the following paths -- you do not need all three.

| Path | Use it when | What you get |
|---|---|---|
| **A. Headless container** (recommended) | You just want to run the integration and read the results. | One self-contained image: pipeline + MySQL + a `repatch` CLI. No GUI, no IDE setup. |
| **B. GUI dev container** | You want to watch RePatch drive IntelliJ, or to step through its code. | A Linux desktop in your browser with the project preloaded in IntelliJ IDEA. |
| **C. Local install** | You cannot run Docker. | Everything on your own machine; the most work. |

#### Path A -- headless container (recommended)

Build the image once from the repository root, then start a long-lived container and open a shell in it. See
[`containers/README.md`](https://github.com/Software-Reengineering/RePatch/blob/RePatch-2.0-upgrade/containers/README.md)
for the full reference.

```bash
git clone -b RePatch-2.0-upgrade https://github.com/Software-Reengineering/RePatch.git
cd RePatch
docker build -f containers/Dockerfile -t repatch-headless .
```

Start it in the background and get a terminal (Linux/macOS; the README gives the PowerShell form):

```bash
docker network create repatch-net        # one-time

docker run -d --name repatch --restart unless-stopped --network repatch-net \
  -e RP_DB_BIND=0.0.0.0 \
  -v repatch-data:/home/repatch/data \
  -v repatch-results:/home/repatch/results \
  -v "$PWD/containers/import":/home/repatch/import \
  --memory 10g --shm-size 1g \
  repatch-headless sleep infinity

docker exec -it repatch bash             # a terminal, any time
```

Inside the container, save a GitHub token once. **No scopes are needed** -- create a classic token at
[github.com/settings/tokens](https://github.com/settings/tokens) with every box unchecked. The pipeline only reads
public PR metadata, but without a token you are capped at 60 API requests/hour and runs stall:

```bash
repatch token            # prompts, verifies, and stores it in the data volume
repatch status           # health check: MySQL up? kafka clone provisioned?
```

Your results and clones live in the two named volumes, not the container, so they survive restarts and rebuilds.

#### Path B -- GUI dev container

Follow
[`docker/dev-container-repatch/README.md`](https://github.com/Software-Reengineering/RePatch/blob/RePatch-2.0-upgrade/docker/dev-container-repatch/README.md):

```bash
cd RePatch/docker/dev-container-repatch
docker compose build --no-cache
docker compose up --build
```

The container runs a Linux desktop in your browser at [http://localhost:3000](http://localhost:3000), with a
shortcut that opens the project in IntelliJ IDEA. Everything is preinstalled: JDK 17 (builds the plugin), JDK 11
(the kafka-era project SDK), IntelliJ IDEA 2024.3.7 Community, Maven, and a RefactoringMiner 2.1.0 build already
in the local Maven repository -- so you can skip the RefactoringMiner steps of Path C. phpMyAdmin is at
[http://localhost:8080](http://localhost:8080) (user `root`, password `root`).

> **Where your edits live.** The copy you work on is the one cloned *inside* the image, at
> `/config/git/RePatch`; it is not connected to any clone on your host. Edits persist in the container's volume,
> so commit and push from inside the container if you want to keep them.

#### Path C -- local install

Follow the "Installation and Running RePatch" section of the
[branch README](https://github.com/Software-Reengineering/RePatch/blob/RePatch-2.0-upgrade/README.md). You need
**JDK 17** to build the plugin, **JDK 11** as well (the kafka evaluation clone pins it as its project SDK), Git,
and MySQL 8. You must also build **RefactoringMiner 2.1.0** and install it into your local Maven repository
first:

```bash
git clone --branch 2.1.0 https://github.com/manuelohrndorf/com.github.tsantalis.refactoringminer
cd com.github.tsantalis.refactoringminer
./gradlew jar          # produces build/libs/RefactoringMiner-2.1.0.jar

mvn install:install-file \
  -Dfile=build/libs/RefactoringMiner-2.1.0.jar \
  -DgroupId=com.github.tsantalis -DartifactId=refactoring-miner \
  -Dversion=2.1.0 -Dpackaging=jar -DgeneratePom=true
```

> RefactoringMiner 2.1.0 ships an old Gradle wrapper that **cannot run on JDK 17** -- build it with JDK 11, for
> example `JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64 ./gradlew jar`. The resulting jar is a plain library and
> the JDK 17 build consumes it fine.

Then open RePatch in IntelliJ IDEA and use **Build → Build Project**.

### 2. Run the integration pipeline

#### Path A -- one command

The CLI takes the PR number directly. Our missed opportunity is `apache/kafka` PR **#13386** going into
`linkedin/kafka`:

```bash
repatch run 13386
```

The first run also provisions the kafka evaluation clone (a one-time ~500 MB checkout plus dependency download),
so expect it to take a while. Results land in the MySQL database `repatch_pr13386`.

Equivalently, you can name the source, target and database label yourself -- useful once you move beyond kafka:

```bash
repatch lab apache/kafka linkedin/kafka 13386     # database: repatch_lab
repatch lab apache/kafka linkedin/kafka 13386 --dry-run   # print the plan and exit
```

Useful flags: `--dry-run`, `--keep-db` (resume, skipping scenarios already done), `--timeout SECONDS`.
Exit code `0` is success; `42` means RePatch degraded to a plain cherry-pick for a scenario (check `repatch log`),
and `124` is a timeout.

#### Paths B and C -- through the IDE

RePatch is an IntelliJ plugin, so it is launched through the Gradle **`:runIde`** task rather than a plain main
class. Create a run configuration (**Run → Edit Configurations**) for `:runIde` and pass these Gradle properties:

```
-Pmode=integration -PdataPath=repatch-integration-projects -PevaluationProject=kafka
```

* `-Pmode=integration` selects the integration pipeline.
* `-PdataPath` names the directory holding the evaluation clones. It is resolved **relative to your home
  directory**, so do not give it a leading `/`: the value above checks out into
  `~/repatch-integration-projects` (`/config/repatch-integration-projects` in the dev container).
* `-PevaluationProject=kafka` is the **target variant** to integrate into -- `linkedin/kafka`, in our case.

Also create `src/main/resources/github-oauth.properties` by copying `github-oauth.properties.template` in the same
directory and adding your token.

The pipeline then needs **two runs**, because the target variant has to be indexed by IntelliJ before it can be
analyzed. This is expected -- do not assume the first run failed.

1. **Start the run configuration.** RePatch clones the target variant and adds the source variant as a remote.
2. When the cloning has finished, **stop the run.** Open the cloned project (`kafka`) in a **separate** IntelliJ
   window; you will find it inside the directory you gave as `-PdataPath` (in the dev container:
   `/config/repatch-integration-projects`).
3. **Wait for IntelliJ to index and build** that cloned project, then close the window.
4. **Re-run** the RePatch run configuration.
5. Wait for the integration pipeline to finish.

No data configuration is needed for the lab: RePatch reads its scenarios from `src/main/resources/sample_data/`,
the default dataset, which contains exactly one row -- `apache/kafka,linkedin/kafka,13386,MO` -- the missed
opportunity you identified in Task 1.

### 3. Configuring your own PRs (project assignments)

For the **project assignments** you will run four PRs of your own.

**Path A.** Put them in a CSV -- column 1 the PR number, column 2 the source, column 3 the target; further columns
are ignored, so use them for notes. Drop the file into `containers/import/` on the host (it is mounted at
`/home/repatch/import`), then run the whole batch under one database label:

```csv
pr,source,target,comment
13386,apache/kafka,linkedin/kafka,the lab PR
12363,apache/kafka,linkedin/kafka
```

```bash
repatch myproject scenarios.csv --dry-run    # check the plan first
repatch myproject scenarios.csv              # run it
```

**Paths B and C.** Two flat files drive the scenario list, and each of `src/main/resources/sample_data/` and
`src/main/resources/complete_data/` holds its own copy:

* `repatch_integration_projects` -- one `source,target` pair per line.
* `repatch_integration_patches` -- one `source,target,pull-request-number,label` row per line (`MO` = missed
  opportunity).

`sample_data` is the single-scenario set used by this lab; `complete_data` is the full dataset from the paper. Select
between them with `-PdataSet`, then rebuild and rerun:

```
-PdataSet=sample     # default -- src/main/resources/sample_data/
-PdataSet=complete   # src/main/resources/complete_data/
```

Note that `-PdataPath` does **not** select the dataset -- it only names the checkout directory. The two are easy to
confuse because they look alike: the dataset *files* are spelled with underscores
(`repatch_integration_patches`), while the clone *directory* uses hyphens (`repatch-integration-projects`). They
are unrelated. Finally, do not run the full `complete` dataset out of curiosity: it is 477 scenarios, tens of
hours and well over 100 GB.

### 4. View the RePatch output

RePatch records, for each PR, the conflicting files, conflict blocks and conflicting lines produced by
**refactoring-aware integration** versus a **plain `git cherry-pick`**. That comparison is the result you are
after.

#### Path A

```bash
repatch runs                  # every run database, with patches done / total
repatch verdicts              # the verdict table for the latest run
repatch verdicts pr13386      # ... or for a named run
repatch log                   # page through the full pipeline log
repatch results 13386         # locate the merged result trees on disk
repatch sql                   # a mysql shell on the run database
```

To browse in a browser instead, start phpMyAdmin on the same docker network (this is why the container was started
with `-e RP_DB_BIND=0.0.0.0`):

```bash
docker run -d --name repatch-pma --restart unless-stopped --network repatch-net -p 8080:80 \
  -e PMA_HOST=repatch -e PMA_USER=repatch -e PMA_PASSWORD=repatch phpmyadmin
```

Then open [http://localhost:8080](http://localhost:8080); each run database (`repatch_pr13386`, `repatch_lab`, …)
is listed on the left.

#### Paths B and C

Results go to the MySQL database **`refactoring_aware_integration_repatch`**, which RePatch creates if it does not
already exist. Connect with phpMyAdmin (dev container: [http://localhost:8080](http://localhost:8080), `root`/`root`),
the MySQL CLI, MySQL Workbench, or DBeaver.

> **Do not confuse it with the published dump.** The repository also ships the paper's own results in
> `database-dump/`, which import into a *separate* database called `refactoring_aware_integration` (see
> [`docker/HOW-TO.md`](https://github.com/Software-Reengineering/RePatch/blob/RePatch-2.0-upgrade/docker/HOW-TO.md)).
> That one is useful for browsing the paper's results without running anything, but it is **not** your run's
> output, and it predates the 2.0 `refactoring_conflict` table.

#### What to look at

The key table is `merge_result`, which records how RePatch reduced or resolved merge conflicts when
`git cherry-pick` failed. The other tables carry supporting metadata and diagnostics: `project`, `patch`,
`merge_commit`, `file_statistics`, `conflicting_file`, `conflict_block`, `refactoring`, and `refactoring_conflict`.

**Quick start (SQL):**

```sql
-- See available tables
SHOW TABLES;

-- Inspect the structure of a table
DESCRIBE merge_result;

-- Preview the integration outcomes
SELECT * FROM merge_result LIMIT 50;
```

To inspect any other table, replace the placeholder below:

```sql
SELECT * FROM <table_name> LIMIT 50;
```

**Questions:**

* Did `git cherry-pick` apply the patch directly, or did RePatch have to invert refactorings first? What does
  `merge_result` tell you?
* Which refactorings did RePatch detect between `apache/kafka` and `linkedin/kafka` around this patch?
* How many conflicting files and conflict blocks would a plain cherry-pick have produced, compared with the
  refactoring-aware integration?

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **Keep It Simple** *(p.37)* -- Avoid unnecessary setup complexity; stick to the minimal environment needed to
  run the integration. This is exactly why the lab runs one scenario headlessly rather than the full dataset.
- **Most Valuable First** *(p.29)* -- Start with the preselected high-impact PR before generalizing to others.
- **Compare Code Mechanically** *(p.227)* -- Rely on automated, tool-driven alignment before manual inspection.
- **Tests: Your Life Insurance** *(p.149)* -- Even after an automated integration, confirm correctness through
  testing (which is exactly what Task 3 is about).

<br/>

Task 3: Writing Tests for the Integrated Change
=========

Task 2 used RePatch to integrate the missed opportunity from **Apache Kafka PR #13386** into the target variant.
Integration at the syntactic level is not enough, though -- we still need to know whether the change behaves
correctly in its new context. In this task you will write the **missing test** for the integrated patch.

Work on the integrated result RePatch produced, not on a fresh checkout. If you ran the headless container,
`repatch results 13386` prints where the merged trees live (conflict markers left in place, with
`repatch-state.bundle` holding the full RePatch-produced state); copy one out with `docker cp` if you would rather
work on the host. If you ran through the IDE, it is the clone under the directory you passed as `-PdataPath` (in
the dev container, `/config/repatch-integration-projects/`), with `apache/kafka` already attached as a
remote.

### 1. Inspect what was actually integrated

The patch touches exactly one file and one method:

* **File:** `connect/runtime/src/main/java/org/apache/kafka/connect/runtime/WorkerSourceTask.java`
* **Method:** `commitOffsets()`
* **Change:** seven occurrences of `committableOffsets` become `offsetsToCommit` -- the guard
  `if (committableOffsets.isEmpty())` and the arguments of the log statements in both branches.

The upstream bug report (KAFKA-14809) explains why this went unnoticed: a few lines earlier, `commitOffsets()`
assigns `this.committableOffsets = CommittableOffsets.EMPTY`, so `committableOffsets.isEmpty()` was **always
true**. Connect therefore logged "no records were produced by the task since the last offset commit" even when it
was committing offsets, and the `else` branch that reports the number of acknowledged and pending messages could
never be reached.

Confirm the divergence for yourself: the same method exists in the target variant at a very different offset
(around line 480 on `linkedin/kafka`'s default `3.0-li` branch, against roughly line 216 in the mainline). This is
the structural divergence RePatch had to align.

### 2. Recognize what kind of test this needs

> **This patch changes no observable behavior.** Offsets are committed identically before and after it; only the
> log messages change. A conventional test that asserts on return values, committed offsets, or metrics will pass
> on the buggy and the fixed version alike, and so proves nothing.

To detect this fix, your test has to **capture log output** and assert on it: that committing a non-empty set of
offsets logs "Committing offsets for N acknowledged messages" rather than the "no records were produced" message.
Getting to this realization is the point of the task -- the upstream PR itself shipped without a test, which is
exactly the gap you are filling.

### 3. Write the test

The mainline shows the idiom. In `apache/kafka`, `WorkerSourceTaskTest` uses a `LogCaptureAppender` in a
try-with-resources block, raises the class logger to `TRACE`, exercises the code, and asserts over
`appender.getMessages()`.

**That template does not port to the target variant as-is** -- which is itself worth noticing:

| | `apache/kafka` (source) | `linkedin/kafka` `3.0-li` (target) |
|---|---|---|
| Test framework | JUnit 5 + Mockito | JUnit 4 + EasyMock/PowerMock, `extends ThreadedTest` |
| Logging backend | log4j2 | log4j **1.2.17** via slf4j-log4j12 |
| `LogCaptureAppender` | `org.apache.kafka.common.utils` (available to Connect tests) | **not available** to `connect:runtime` |

In the target, a reusable log-capture helper exists only in modules you cannot import from Connect tests:
`core/.../kafka/utils/LogCaptureAppender.scala` and
`streams/src/test/java/org/apache/kafka/streams/processor/internals/testutil/LogCaptureAppender.java`. The streams
one is a small, self-contained log4j 1.x `AppenderSkeleton implements AutoCloseable` -- use it as the model for a
test-scoped appender of your own under `connect/runtime/src/test/java/`.

So:

1. Add your test to `connect/runtime/src/test/java/org/apache/kafka/connect/runtime/WorkerSourceTaskTest.java`,
   following the conventions of the **target** repository (JUnit 4, EasyMock/PowerMock), not the mainline's.
2. Arrange a `commitOffsets()` call with a non-empty set of offsets to commit.
3. Capture the log output of `WorkerSourceTask` and assert that the "Committing offsets for ... acknowledged
   messages" message is present.
4. Sanity-check your test: revert the patched lines, confirm the test **fails**, then restore them and confirm it
   passes. A log-assertion test that cannot fail is worthless.

### 4. Run it

Run only the affected module and class. Kafka's full test suite takes hours and you do not need it:

```bash
./gradlew :connect:runtime:test --tests "org.apache.kafka.connect.runtime.WorkerSourceTaskTest"
```

Build the **kafka clone with JDK 11**, not JDK 17: it is a Kafka-3.0-era project and its IDE model pins JDK 11 as
the project SDK. (JDK 17 is what builds RePatch itself -- a different thing.) Both containers carry both JDKs; set
`JAVA_HOME` accordingly if the build complains about the toolchain.

If the test fails to compile or run, investigate whether the integration requires further adaptation to the target
variant -- and record what you had to change.

**Questions:**

* Why can this patch not be verified by asserting on committed offsets or on metrics?
* What did you have to adapt to move the mainline's testing approach into the target variant? Was the obstacle the
  patch itself, or the divergence in test infrastructure?
* Does your test fail on the unpatched code? If not, what is it actually asserting?
* RePatch reports that the patch integrated successfully. Does a successful integration tell you anything about
  whether the patched code is correct?

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **Tests: Your Life Insurance** *(p.149)* -- Tests protect against regressions and confirm the correctness of the
  integration.
- **Write Tests to Understand** *(p.179)* -- Writing the test is what forces you to work out what the patch does
  and does not change.
- **Grow Your Test Base Incrementally** *(p.159)* -- Add one test around the integrated patch instead of rewriting
  the suite; run one class, not the whole build.
- **Study the Exceptional Entities** *(p.107)* -- Focus your tests on the edge cases and unusual conditions where
  bugs are most likely -- here, the branch that was previously unreachable.

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
