---
layout: page
title: Mining Software Repositories
permalink: /teaching/CS473-Fall2022/msr/
---

<form action="/teaching/CS473-Fall2022/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>
<form action="/teaching/CS473-Fall2022/metrics/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Metrics and Visualization" />
</form>
<form action="/teaching/CS473-Fall2022/refactoring/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Refactoring Assistants" />
</form>
<form action="/teaching/CS473-Fall2022/integration/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Software Integration" />
</form>
<form action="/teaching/CS473-Fall2022/dynamic/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Dynamic Analysis: Testing" />
</form>
<form action="/teaching/CS473-Fall2022/msr/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Mining Software Repositories" />
</form>
<form action="/teaching/CS473-Fall2022/project/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Reengineering Project" />
</form>

<br/>
<br/>




Mining software repositories is related to both data mining and reverse engineering. 
Source control repositories, bug repositories, archived
communications, deployment logs, and code repositories
are examples of software repositories that are commonly
available for most software projects. The Mining Software
Repositories (MSR) field analyzes and cross-links the rich
data available in these repositories to uncover interesting
and actionable information about software systems. By
transforming these repositories from static record-keeping
ones into active repositories, we can guide decision processes 
in modern software projects. For example, data in
source control repositories, traditionally used to archive
code, could be linked with data in bug repositories to help
practitioners propagate complex changes and to warn them
about risky code based on prior changes and bugs. 
[Ahmed E. Hassan. 2008](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=4659248). 
In this lab you will mine software repositories, extract and analyze some interesting 
software artifacts archived in the repositories.

Material and Tools
==========
* Session slides [here]().
* The following GitHub repos you can use to run the lab experiments
  * [scottyab/rootbeer](https://github.com/scottyab/rootbeer)
  * [Skyscanner/backpack](https://github.com/Skyscanner/backpack) (Try it from home since it has very many commits)
  * [mendhak/gpslogger](https://github.com/mendhak/gpslogger) (Try it from home since it has very many commits)
  * [thundernest/k-9](https://github.com/thundernest/k-9) (Try it from home since it has very many commits)
* Resources of how to obtain data on GitHub
  * [GitHub API](https://docs.github.com/en/rest)
  * [How to create GitHub token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token#creating-a-token) or you could use this [Generate Token](https://github.com/settings/tokens/new?scopes=repo) if you do not want to read  details.

Steps/Preparations
==========
The following tasks will guide you to carryout the labs of mining software repositories. 
In the class slides, we have looked at three ways how we can get data from GitHub: 
cloning the repos using Git, using [GHTorrent](https://ghtorrent.org/) and using the 
[GitHub API](https://docs.github.com/en/rest). In this lab we shall go through getting GitHub data using the
[GitHub API](https://docs.github.com/en/rest).

Task 1
=======
* Create a GitHub token(s) by following the tutorial on the link. Each token corresponds to a GitHub account.


