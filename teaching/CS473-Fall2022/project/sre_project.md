---
layout: page
title: Reengineering Project - linkedin/kafka
permalink: /teaching/CS473-Fall2022/project/
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
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Mining Software Repositories" />
</form>
<form action="/teaching/CS473-Fall2022/project/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Reengineering Project" />
</form>

<br/>
<br/>

Target Application
==============
[LinkedIn](https://github.com/linkedin/kafka) project is a variant fork of [Apache Kafka](https://github.com/apache/kafka) running at LinkedIn. 

Kafka was born at LinkedIn. The run thousands of brokers to deliver trillions of messages per day. They run a slightly modified version of Apache Kafka trunk. The [LinkedIn](https://github.com/linkedin/kafka) variant contains the LinkedIn Kafka release.

Assignment
==========

### 1. Contextualization of the Project

LinkedIn is a clone-and-own variant of Apache Kafka that was created by copying and adapting the existing 
code of Apache Kafka that was forked on 2011-08-15T18:06:16Z. The two software systems kept on synchronizing 
their new updates until 2022-02-22T13:32:39Z. Since 2022-02-22T13:32:39Z (divergence date), the two 
projects do not share common commits yet actively evolve in parallel. Currently (2022-02-28T15:01:39Z), 
LinkedIn has 500 individual commits, and Apache Kafka has 3,103 individual commits. Development becomes 
redundant with the continued divergence, and maintenance efforts rapidly grow. For example, if a bug is 
discovered in a shared file and fixed in one variant, it is not easy to tell if it has been fixed in the 
other variant.

### 2. Getting Started Instructions
Please pay attention to the following instructions. You need to send an email to <em></em><a href="mailto:john.businge@unlv.edu">me</a> with:
* Subject "Reengineering - Linkedin". 
* Message Body:
  * The full name of the members in your group (including yours). Remember, a maximum of 3 
  people, but you are allowed to work with less than 3 if you want to.
  * Attach the **pre-conditions report** (PDF format) in your message.

* Your Pre-conditions Report should contain the following:
  * Project Name
  * Full names of all the members in your group
  * Link to your GitHub repositories (which shows you already forked [LinkedIn])
  * The members are set as collaborators to the GitHub project.
  * Invite me as collaborator (my [GitHub Id - ```johnxu21```](https://github.com/johnxu21)).
  * 


