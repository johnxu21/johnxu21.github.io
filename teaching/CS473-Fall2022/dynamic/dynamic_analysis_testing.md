---
layout: page
title: Dynamic Analysis- Testing
permalink: /teaching/CS473-Fall2022/dynamic/
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
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Dynamic Analysis: Testing" />
</form>
<form action="/teaching/CS473-Fall2022/msr/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Mining Software Repositories" />
</form>
<form action="/teaching/CS473-Fall2022/project/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Reengineering Project" />
</form>

<br/>
<br/>

Dynamic analysis is “the analysis of the properties of a running software system” [[Ball1999](https://ansymore.uantwerpen.be/system/files/Ball1999.pdf)]. It is complementary to static analysis techniques. Some properties that cannot be studied through static analysis can be examined with dynamic analysis and vice versa. The applications of dynamic analysis techniques are very broad: program comprehension, system verification, resource profiling, test analysis, etc. In this session, we focus on one very important aspect of dynamic analysis: Testing.

As the chapter so eloquently states, "Tests: Your Life Insurance!" (OORP, p.149). Tests are essential for Reengineering activities. They can help you: (1) to reveal unwanted side effects of refactoring ("Write Tests to Enable Evolution", OORP, p.153); and (2) to understand the inner workings of a system ("Write tests to Understand", OORP, p.179). 

The presence of automated tests does however not offer any guarantee about its quality. Do the tests cover the whole system or are some parts left untested? Which parts are covered to which extend? Hence, measuring test coverage is a useful, even necessary, way to assess the quality and usefulness of a test suite in the context of reengineering.