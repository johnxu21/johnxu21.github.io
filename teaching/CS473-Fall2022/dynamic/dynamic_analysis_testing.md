---
layout: page
title: "Dynamic Analysis: Testing"
permalink: /teaching/Software-Reengineering/dynamic/
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
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
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
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Reengineering Project" />
</form>

<br/>
<br/>

Dynamic analysis is "the analysis of the properties of a running software system" [Ball, 1999]. It is
complementary to static analysis: some properties that cannot be studied statically can be examined dynamically,
and vice versa. The applications of dynamic analysis are broad -- program comprehension, system verification,
resource profiling, test analysis, and more. In this session, we focus on one very important aspect of dynamic
analysis: **testing**.

As the chapter so eloquently states, "**Tests: Your Life Insurance!**" (OORP, p.149). Tests are essential for
reengineering activities. They help you (1) reveal unwanted side effects of refactoring
("**Write Tests to Enable Evolution**", OORP, p.153) and (2) understand the inner workings of a system
("**Write Tests to Understand**", OORP, p.179).

The presence of automated tests does not, however, offer any guarantee about their quality. Do the tests cover
the whole system, or are some parts left untested? Which parts are covered, and to what extent? Measuring test
coverage is therefore a useful -- even necessary -- way to assess the quality and usefulness of a test suite in
the context of reengineering.

**In this session you will:**

* measure statement and branch coverage of an existing test suite with Coverage.py;
* write a new test and observe its effect on coverage;
* compare the coverage views offered by Coverage.py and SonarQube;
* argue what level of coverage is good enough before you start reengineering.

Materials & Tools Used for this Session
===============

**Slides**

* [Dynamic Analysis: Testing (PDF)](../../../files/Testing.pdf)

**Projects**

* [pacman-python](https://github.com/Software-Reengineering/pacman-python) -- the same small Python game used in
  the [Metrics and Visualization](/teaching/Software-Reengineering/metrics/) session.
* [django CMS](https://github.com/django-cms/django-cms)

**IDE**

* [PyCharm](https://www.jetbrains.com/pycharm/) -- the Community Edition is sufficient; any other IDE works as well.

**Tools**

* [Coverage.py](https://coverage.readthedocs.io/en/7.10.6/) -- a code coverage tool supported by PyCharm. You may
  use another coverage tool at your discretion, but it may require some adaptation for the projects we use in the
  lab sessions.

**Book**

* [Object-Oriented Reengineering Patterns](http://scg.unibe.ch/download/oorp/) (OORP)
  (_Note: OORP, p.xx refers to a page in the pdf version of this book_)

Auxiliary Tools
==========
Auxiliary tools are not required for the lab session itself, but they may give you additional information (or
alternatives) about a project. Use them at your own discretion.

* [SonarQube](https://www.sonarsource.com/products/sonarqube/) -- a platform that performs static analysis on
  source code. It can also display test coverage data produced by dynamic analysis tools.
* [Pynguin](https://github.com/se2p/pynguin) -- a test generation tool for Python; it automatically generates unit
  tests.

<br/>

Setup / Preparation
==============

1. **Install Coverage.py:**

   ```bash
   pip install coverage
   ```

2. **Complete the setup and the tasks from the
   [Refactoring Assistants](/teaching/Software-Reengineering/refactoring/) lab** -- in particular Task 2, where you
   install and run SonarQube. You will need it again in Task 3 below.
3. As usual, you also need PyCharm and a local clone of the projects.
4. **Download the book**, if you have not already:
   "[Object-Oriented Reengineering Patterns](http://scg.unibe.ch/download/oorp/)".

> **Tip:** take screenshots of every coverage report you generate. You will need them to answer the questions
> below and as evidence of tool usage for the
> [Intermediate Report](/teaching/Software-Reengineering/project/).

<br/>

Task 1: Test Coverage with Coverage.py
===========
We begin by measuring the coverage of the existing pacman-python test suite with
[Coverage.py](https://coverage.readthedocs.io/en/7.10.6/). Remember to install the tool as described in the
**Setup / Preparation** section above.

First, make sure you can run the tests from the PyCharm terminal. To run the unit tests with coverage:

```bash
python -m coverage run refactored/pacman_unittests.py
python -m coverage html
python -m coverage erase
```

And for the integration tests:

```bash
python -m coverage run refactored/program_integration_tests.py
python -m coverage html
python -m coverage erase
```

This produces an HTML coverage report with **statement coverage** under the `htmlcov` directory. Rename the
generated folder for each run (unit and integration) so that the reports are not overwritten.

Coverage.py measures statement coverage by default, but other coverage criteria are available for assessing the
adequacy of your tests. To add **branch coverage** to the report, pass the `--branch` flag. For the unit tests:

```bash
python -m coverage run --branch refactored/pacman_unittests.py
python -m coverage html
python -m coverage erase
```

And for the integration tests:

```bash
python -m coverage run --branch refactored/program_integration_tests.py
python -m coverage html
python -m coverage erase
```

If everything runs without errors, you will again find an HTML report under `htmlcov`. Rename the generated folder
for each of the two branch-coverage runs as well, and keep these four reports (or screenshots of them) -- you will
need them for the questions below.

**Questions:**

* Is the coverage good enough?
* If you make changes to the pacman-python sources, can you rely on the current tests to catch faults?
* Are the statement coverage results similar to the branch coverage results? Why, or why not?
* Can you apply the same procedure to the django CMS project? What are your observations?

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **Tests: Your Life Insurance** *(p.149)* -- Tests act as a safety net during reengineering. Coverage analysis
  shows where the safety net is strong and where it has holes, before you make any changes.
- **Grow Your Test Base Incrementally** *(p.159)* -- Expand your tests in small, safe steps. Running both
  statement and branch coverage gives you the baseline for that incremental improvement.
- **Test the Interface, Not the Implementation** *(p.171)* -- Verify observable behavior rather than internal
  details. When reading coverage, look for missing behavioral scenarios, not untested private helpers.

<br/>

Task 2: Increasing Coverage on pacman-python
===================
For the second task, we will increase the statement and branch coverage of **pacman-python**. Doing so is simple:
we just need to write more tests. In this task, you will write one new test case.

Let's create a unit test for a single method: the `move_ghosts` function in `pacman.py`, in the **refactored**
folder. Use `pacman_unittests.py` (also in the **refactored** folder) as a template for your test case.

After adding the new test, run `pacman_unittests.py` again with coverage. If your test has no errors, you will see
the updated coverage report. Keep this report (or a screenshot) -- you will need it to answer the questions below.

**Questions:**

* How did the new test affect the coverage?
* Do you think 100% coverage is feasible?
* What would you propose as a good level of code coverage?

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **Write Tests to Understand** *(p.179)* -- When you need to understand how a part of the system works,
  especially when it is poorly documented, write a small, focused test that captures your understanding. The test
  acts as both documentation and a safety net for future changes. Your test for `move_ghosts` will teach you
  exactly how the method behaves and record that knowledge so that you can verify it later.
- **Grow Your Test Base Incrementally** *(p.159)* -- One well-chosen test at a time is how a usable test suite
  gets built on a system that has none.

<br/>

Task 3: SonarQube Coverage Information on pacman-python
===========
SonarQube is a static analysis tool, but it can also display the results of test coverage in its interface.
First, start SonarQube as described in Task 2 of the
[Refactoring Assistants](/teaching/Software-Reengineering/refactoring/) lab, and make sure the SonarQube service
is running. Then follow the SonarQube documentation on
[Python test coverage](https://docs.sonarsource.com/sonarqube/9.8/analyzing-source-code/test-coverage/python-test-coverage/)
to feed your Coverage.py report into SonarQube.

**Questions:**

* What do you think of the coverage overview visualization provided by SonarQube?
* Which did you find better for visualizing the source code: statement coverage, branch coverage, or SonarQube?

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **Tests: Your Life Insurance** *(p.149)* -- A coverage dashboard is only useful if it changes what you test
  next; use it to decide where the safety net still needs work.

Post-Lab Quiz: Dynamic Analysis -- Testing
==========
The quiz for this session is posted on WebCampus.
