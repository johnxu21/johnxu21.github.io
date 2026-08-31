---
layout: page
title: Metrics and Visualization
permalink: /teaching/Software-Reengineering/metrics/
---

<form action="/teaching/Software-Reengineering/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>
<form action="/teaching/Software-Reengineering/metrics/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
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
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Reengineering Project" />
</form>

<br/>
<br/>

The purpose of the laboratory exercises in general is to stimulate discussion about the properties of a 
well-structured object-oriented design. The tasks and assignments are designed to stimulate your comprehension 
of the topic and the tools. In most cases, you can use alternative projects and/or tools to accomplish the same 
or similar tasks, or even more!

This first session gives you your first contact with the sample projects and the tool suite. Consider the tools 
used in this session as providers of the data you need to build up an argument for a system report or an action plan.

**In this session you will:**

* get acquainted with two very different visualization tools, CodeScene and JSCity;
* make your "**First Contact**" (OORP, p.39) with a small system (pacman-python) and a large one (django CMS);
* use metrics and visualizations to spot candidate reengineering targets ("**Study the Exceptional Entities**", OORP, p.107);
* argue when such visualizations help you plan refactoring work -- and when they do not.

Materials & Tools Used for this Session
========

**Slides**

* [Metrics and Visualization (PDF)](../../../files/metrics_and_visualization.pdf)

**Projects**

* [pacman-python](https://github.com/Software-Reengineering/pacman-python) -- a small Python game, shipped in three
  variants: `spaghetti/`, `refactored/` and `oop/`.
* [django CMS](https://github.com/django-cms/django-cms) -- a large, actively maintained Python system.

**IDE**

* [PyCharm](https://www.jetbrains.com/pycharm/) -- the Community Edition is sufficient; any other IDE works as well.

**Tools**

* [CodeScene](https://codescene.com/) -- **no** installation necessary, but it requires a GitHub account. CodeScene is
  free for public (open-source) repositories, and its GitHub integration lets it visualize the repositories in your account.
* [JSCity](https://github.com/ASERG-UFMG/JSCity/wiki/JSCITY) -- an implementation of the Code City metaphor for JavaScript code.

**Book**

* [Object-Oriented Reengineering Patterns](http://scg.unibe.ch/download/oorp/) (OORP)
  (_Note: OORP, p.xx refers to a page in the pdf version of this book_)

<br/>

Setup / Preparation
=============

1. **Fork the project you want to analyze into your own GitHub account.** CodeScene builds its projects from the
   repositories it can see through your GitHub login, so the repository has to live in your account.
2. **Log into CodeScene.** Go to [CodeScene](https://codescene.com/) and use the "Log in" menu (top-right corner);
   you can choose the option "Log in with GitHub". Once logged in, create a new project: CodeScene shows all the
   GitHub projects in your account. Select your fork of pacman-python, start the analysis, and continue with the
   next step while it runs (it might take a while, depending on the project).
3. **Clone the same project and open it in the IDE of your choice** (for example, PyCharm). Build and run the
   project; refer to the project README if necessary (the commands for pacman-python are given below).
4. **Download the book**, if you have not already: "[Object-Oriented Reengineering Patterns](http://scg.unibe.ch/download/oorp/)".

To get pacman-python running locally:

```bash
git clone https://github.com/<your-github-account>/pacman-python.git
cd pacman-python
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

> **Tip:** take screenshots while you work. You will need evidence of tool usage for the
> [Intermediate Report](/teaching/Software-Reengineering/project/) later in the semester.

<br/>

Task 1: Warm-Up -- Visualizing React
============
This first task has two goals:

* to help familiarize yourself with the CodeScene interface; and
* to observe that not every visualization is useful for refactoring.

Open the CodeScene [demo projects](https://codescene.io/demo-projects). These are examples (from a full version of
CodeScene and not only the free version we are using) of projects analyzed by CodeScene. Select the **React**
project and look at the visuals presented.

Then visit the [JSCity](https://github.com/ASERG-UFMG/JSCity/wiki/JSCITY) wiki and look at the example cities.
You may want to select a simple example first, such as [clumsybird](https://aserg-ufmg.github.io/JSCity/?id=10),
to get acquainted with the navigation (use the mouse scroll to zoom in/out). After that, also open the
[React](https://aserg-ufmg.github.io/JSCity/?id=47) city -- and be patient, because it may take a while to load.
Remember how JSCity maps code to a city: folders are districts, files are sub-districts, functions are buildings,
the number of lines of code gives a building its height, and the number of variables its base size.

**Questions:**

- What did you think of these visualization tools?
- Which information about the visualized project can you extract from each of them?
- Which of the two visualizations would be more useful to plan refactoring activities? Why?

<br/>

Task 2: First Contact -- pacman-python
===============
For the second task, the goal is to start getting acquainted with the pacman-python source code.
Clone the repository (if you did not already do so during the setup) and run the application. Now look at the
source code and other files in the project, and try to understand its internal structure. Note that the repository
holds three implementations of the same game -- `spaghetti/`, `refactored/` and `oop/` -- so read them side by side.

As stated in the book (OORP, p.39), this is your "**First Contact**" with the software that needs
reengineering activities. As often, we ask ourselves "**Where do I start?**" (OORP, p.40).

pacman-python is a Python implementation that is supposed to replicate the original
[Pac-Man game](https://en.wikipedia.org/wiki/Pac-Man).

**Questions:**

- What features are missing in pacman-python (compared to the original)?
- Is it possible to implement those features right now, or should we reengineer the project first to make adding
  the new features easier? (The question is rhetorical for this task, but it is exactly the one you must answer in
  your reengineering project.)
- How do the three variants of the game differ, and which one would you rather extend?

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **First Contact** *(p.39)* -- Your first encounter with an unfamiliar system. Running the program and browsing its
  files is how you build the initial impression that every later decision rests on.
- **Read all the Code in One Hour** *(p.53)* -- A time-boxed reading pass over the whole system. pacman-python is
  small enough that this is realistic; note down the code smells and questions that jump out at you.

<br/>

Task 3: Initial Understanding -- pacman-python in CodeScene
===================
The third task is to use our visualization tool of choice (CodeScene) to identify possible reengineering targets.
Since we already had the "**First Contact**", now we should move to the "**Initial Understanding**" (OORP, p.83)
of the system. One important reengineering pattern here is to "**Study the Exceptional Entities**" (OORP, p.107).

Open the analysis of your pacman-python fork in CodeScene and explore the code health, hotspot, and complexity views.

**Questions:**

- Using CodeScene, can you identify artifacts that appear to be out of place?
- Could they benefit from refactoring activities?
- How do the complexity measurements of such artifacts compare to the others?
- Does what the tool flags match the impression you formed while reading the code in Task 2? Where do they disagree?

**Related Patterns from _Object-Oriented Reengineering Patterns_ (OORP)**

- **Initial Understanding** *(p.83)* -- Build a first model of the system from the data you can gather, rather than
  from what the documentation claims.
- **Study the Exceptional Entities** *(p.107)* -- Measure the system and look at the outliers: the largest, the most
  complex, and the most frequently changed artifacts are your first reengineering candidates.
- **Most Valuable First** *(p.29)* -- Not every exceptional entity is worth the effort. Rank the candidates by the
  value that fixing them delivers.

<br/>

Task 4: Another Project -- django CMS
=============
Repeat Tasks 2 and 3 on the [django CMS](https://github.com/django-cms/django-cms) project: fork it, run the
CodeScene analysis (it is a far larger system, so expect the analysis to take considerably longer), and browse the
source code in your IDE.

**Questions:**

- Which parts of django CMS stand out as exceptional entities?
- Did the tools help you more, or less, than on pacman-python? Why?
- Reading all the code in one hour is realistic for pacman-python. What do you do instead on a system the size of
  django CMS?

<br/>

Discussions and Conclusion
============
We have used metrics and visualization for the Initial Understanding, thereby demonstrating their
potential support to the reengineering process.

- Did the metrics and visualization tools used in this lab session provide you with the information you needed to
  fulfill the goals of the different reengineering patterns?
- Set up an argument about the issues concerning the use of such tools: when would you use them, when wouldn't you?
- Can you envision other usages of these tools in other phases of the reengineering lifecycle?

Post-Lab Quiz: Metrics & Visualization
==========
The quiz for this session is posted on WebCampus.
