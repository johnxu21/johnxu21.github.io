---
layout: page
title: CS472 - Leveraging ChatGPT in Software Engineering Tasks - Lab
permalink: /teaching/CS472/Timetable/GPT/
---
<div class="main-component">
<form action="/teaching/CS472/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Course Overview" />
</form>

<form action="/teaching/CS472/Timetable/">
    <input type="submit" style="background-color:firebrick;color:white;width:185px;
height:40px;" value="Timetable" />
</form>
<form action="/teaching/CS472/Exam/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Exam" />
</form>
<form action="/teaching/CS472/project/">
    <input type="submit" style="background-color:cornflowerblue;color:white;width:185px;
height:40px;" value="Project" />
</form>
</div>
<br/>

Labs
=======
<div class="main-component">
<form action="/teaching/CS472/Timetable/Git_and_GitHub/">
    <input type="submit" style="background-color:#008CBA;float:left; color:white;width:130px;
height:30px;" value="Git & GitHub" />
</form>
<form action="/teaching/CS472/Timetable/dynamic_analysis/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="Testing" />
</form>
<form action="/teaching/CS472/Timetable/CI/">
    <input type="submit" style="background-color:#008CBA;float:left;color:white;width:130px;
height:30px;" value="CI" />
</form>
<form action="/teaching/CS472/Timetable/GPT/">
    <input type="submit" style="background-color:firebrick;float:left;color:white;width:130px;
height:30px;" value="ChatGPT" />
</form>
</div>

<br/>
<br/>

### **This individual assignment is due Oct 1st, 2024**

In this lab, you will learn how to leverage ChatGPT, a powerful language model developed by OpenAI, 
to address various software engineering tasks. ChatGPT, part of the GPT (Generative Pre-trained Transformer) 
family of models, is capable of understanding and generating human-like text based on its input. 
Throughout this lab, you will explore different ways developers incorporate ChatGPT into their workflow and 
complete tasks in software engineering. **The lab will guide you on the responsible use of ChatGPT to improve productivity in software engineering** 

Overview of ChatGPT in Software Engineering
=======
ChatGPT is being used extensively in software engineering due to its natural language understanding and 
generation capabilities. Developers utilize ChatGPT for a wide range of tasks across the software development 
life cycle (SDLC), including requirements engineering, software design, development and implementation, 
quality assurance, maintenance, and management. Some common tasks include code generation, code search, 
test generation, code review, and more.

Details of the definition of the tasks and how LLMs have been used to address the tasks
can be found in **Section 6** of the paper, Hou at al. [LLMs for SE: A SLR](https://arxiv.org/pdf/2308.10620.pdf)

1. Requirements engineering tasks e.g.,
  * Anaphoric ambiguity treatment
  * Requirements classification
2. Software design tasks, e.g.,
  * GUI retrieval
  * Rapid prototyping
3. Software development and implementation tasks, e.g.,
  * Code generation
  * Code search
  * Code documentation
  * Code understanding
  * Program synthesis
4. Software quality assurance tasks, e.g.,
  * Test generation
  * Failure-inducing test Identification
5. Software maintenance tasks, e.g.,
   * Code review
   * Duplicate bug report detection
6. Software management tasks, e.g.,
  * Effort estimation

The figure below presents a typical GitHub PR workflow augmented with ChatGPT interactions, which can originate from either the PR author or a reviewer. 
<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/illustration.png" alt="ShareChatGPTConversations" style="max-width:500px;max-height:500px;" align="center"></p>
Consider a scenario where a developer, intending to fix a bug, add a feature, or enhance an existing one, initiates a change to a file named ```Foo```. Using pull-based development workflow, this process starts with the creation of a new branch and committing the changes. During development, the developer might encounter challenges or seek optimal solutions, prompting them to consult ChatGPT. The response from ChatGPT might be textual or might include a code snippet. Based on the nature of the response, the following scenarios can arise.

1. When the response includes a code snippet, the developer may apply this directly to Foo as a patch, either as provided or after modifications. This scenario is labeled as **"Patch Applied (PA)"**.
2. If the code snippets are not applied, or modified beyond recognition (resulting in a semantic clone), Foo may remain unchanged or include changes influenced by the discussed concepts. This scenario is defined as **"Patch Not Applied (PN)"**.
3. If the interaction with ChatGPT involves only textual advice without code snippets, similar to the previous scenario, Foo may remain unchanged or may be modified based on the guidance received. This scenario is referred to as **None Existing Patch (NE)**

This [research paper](ASE_Paper_2024.pdf) published in the 2024 in the International Conference of Automated Software Engineering is part of our work in studying how developers are actively utilizing ChatGPT. We provide detailed explanations and findings related to the above scenarios. For PA scenario, we used clone detection to determine if code snippet suggested by ChatGPT was integrated in the pull request. For PN and NE cases, we applied qualitative analysis using card sorting to identify interest themes to justify why patch suggested by ChatGPT was not applied and how they utilized textual advice. We found interesting themes as shown below;

## PN Themes:
- **Adaptation to project needs:** Conceptual advice from ChatGPT adapted for customized solutions fitting unique project needs. Highlights the customization of these insights for specific project needs
- **Methodological guidance:**  ChatGPT's advice informed approaches or refined solutions, not directly applied as patches. Focuses on the broader approach or strategy influenced by ChatGPT
- **Specific functionality enhancements:** Enhancements informed by ChatGPT insights, tailored to specific functionality rather than direct patches.
- **Technical limitations:** Non-application of patches due to technical constraints or preference for alternative solutions.
- **Clarification & correction:** Clarifications or corrections led to refining approaches rather than applying new patches.

## NE Themes:
- **Conceptual Guidance & Theoretical Advice:** Discussions focused on programming concepts, design principles, optimization strategies, and the importance of clear naming in code and documentation to enhance readability and maintainability, emphasizing theoretical advice and best practices without specific code implementations.
- **Documentation & Localization Enhancements:** Discussions focused on enhancements in documentation clarity, communication refinement, and localization accuracy, highlighting efforts in making content accessible and understandable to diverse audiences, thereby improving overall documentation quality and effectiveness.
- **Education and Knowledge Sharing:** Sharing knowledge on programming concepts, language-specific features, or explaining code functionalities, serving an educational purpose and enhancing understanding of complex concepts.
- **Debugging & Optimization Strategies:** Centered on debugging methods, performance optimization, and refining algorithms, offering strategic insights into problem-solving approaches without specific code snippets.

In the next three sections, we will look at some **concrete examples for each of the scenarios mentioned above**. We demonstrate how developers incorporate code and how they utilized textual advice without code snippets from ChatGPT. The examples will also correspond to themes and software engineering tasks mentioned earlier.

## Patch Applied (PA)
### **Example 1: Code Duplication and Refactoring**
In this example, a developer uses ChatGPT in the `Software Engineering` activity of `Software maintenance` to address the task of `code duplication and refactoring` in the code. 
Here is the link to both the PR and ChatGPT conversation.


- PR: [https://github.com/nbd-wtf/nostr-tools/pull/241](https://github.com/nbd-wtf/nostr-tools/pull/241)
- ChatGPT Link: [https://chat.openai.com/share/f09f38e5-f541-4f98-9483-e183f5650398](https://chat.openai.com/share/f09f38e5-f541-4f98-9483-e183f5650398)

After reviewing the ChatGPT link and the associated GitHub pull request, it appears that the 
developer is addressing the Software Engineering task of `code duplication`. The ChatGPT prompts indicate a concern about code 
repetition and a desire to refactor or improve the existing code.

The GitHub pull request link shows changes made to the codebase, particularly in the `nostr-tools` project. 
The changes involve modifying existing code to address **duplication issues** and improve the overall code 
quality. Code duplication is a common issue in software development that can lead to maintenance challenges, 
increased likelihood of bugs, and reduced readability. The developer is using ChatGPT to seek advice on how to best approach and 
implement these code changes, demonstrating a typical scenario where AI assistance can enhance 
the efficiency of **code maintenance** tasks.

**Developer prompt** 
```angular2html
I have some duplication in my TypeScript code. I resolve it, I want to create a discriminated union based
on the keys and values of the interface. My code is blow. Is it possible to do what I want?
```
<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/example-1-1.png" alt="ShareChatGPTConversations" style="max-width:700px;max-height:700px;" align="center"></p>

GitHub [file diff](https://github.com/nbd-wtf/nostr-tools/pull/241/files#diff-98476df5961449c9b87e4a05e4cf190b90d14815cb1b23f1e2d5398467287b61)
<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/example-1-2.png" alt="ShareChatGPTConversations" style="max-width:1000px;max-width:1000px;" align="center"></p>

### **Example 2:  Deployment documentation**
In the software development process, various types of documentation play distinct roles in facilitating 
effective communication, collaboration, and understanding. These documents cater to different stakeholders 
and serve diverse purposes, for example:
* *Requirements Documentation*: Describes functional and non-functional specifications.
* *Design Documentation*: Details system architecture, data flow, and component specifications.
* *Technical Documentation*: Provides in-depth technical details about code, APIs, algorithms, and data structures.
* *Testing and QA Documentation*: Describes test plans, cases, and quality assurance processes.
* *Deployment Documentation*: Guides administrators on deploying and configuring software in a production environment.

In this example, the developer used ChatGPT with the following [prompt](https://chat.openai.com/share/7538b618-c08d-45b7-a4ed-bb168e9c1eb0),
and appears to seek assistance in creating user-friendly and concise documentation for the `release.sh` script. 
This would likely fall under the umbrella of deployment documentation, helping system administrators and 
DevOps teams understand how to effectively use the script for software releases.

**Developer prompt:** 
```angular2html
Act as an enthusiast developer advocate with 5 years of experience.
Write a quick documentation about this `release.sh` bash script. What does it do? Use bullets points.
How do we use it? Use short sentences. Add emojis where needed.
```

<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/example-2-1.png" alt="ShareChatGPTConversations" style="max-width:550px;max-height:550px;border:'1px solid black;" align="center"></p>
<br />

As you can observe, the [CONTRIBUTION.md](https://github.com/swarmion/swarmion/pull/678/files#diff-eca12c0a30e25b4b46522ebf89465a03ba72a03f540796c979137931d8f92055) file was updated by simply copying the documentation written by ChatGPT. This documentation is intended to ease the process of on-boarding new contributors to the project
<p style="text-align:center">
<img src="/teaching/CS472/Timetable/GPT/example-2-2.png" alt="ShareChatGPTConversations" style="max-width:550px;max-height:550px;" align="center">
</p>

The link to PR and ChatGPT conversation is provided below:
- PR [Link](https://github.com/swarmion/swarmion/pull/678)
- ChatGPT [Link](https://chat.openai.com/share/7538b618-c08d-45b7-a4ed-bb168e9c1eb0)

### **Example 3: Configuring GitHub Actions workflow**
In Examples 1 and 2 above, the developer used the code generated by ChatGPT "as-is." 
However, this example demonstrates another use case where the developer integrates 
only a *portion* of the code snippet suggested by ChatGPT. The prompt provided by the 
developer aligns with `Configuring GitHub Actions workflow` task which falls under the
`Software Engineering` activity of `Software Configuration Management (SCM)` task. 
SCM encompasses version control, configuration management, and process management.
Configuring GitHub Actions workflow specifically relates to the automation of building, 
testing, and deploying code changes, which aligns with CI practices.

In the context of the use case, after reviewing the GitHub link and ChatGPT conversation, we can see that the developer is seeking 
guidance on setting up and configuring `GitHub Actions workflows` for the `Faker.js` library. The GitHub link specifically shows changes made to the `GitHub Actions workflow` configuration file.


**Developer prompt 1:** 
```angular2html
Write a GitHub Action yml file that blocks the PR from merging when there is a label
named "do NOT merge yet" or "s: on hold"
```
**Developer prompt 2:** 
```angular2html
How can I check "s: on hold" with "contains" using "github.event.pull_request.labels.*.name"
```
Below is the final code snippet generated by ChatGPT and the portion integrated in GitHub pull request.

<p style="text-align:center">
<img src="/teaching/CS472/Timetable/GPT/use-case-2-example-3-1.png" alt="ShareChatGPTConversations" style="max-width:800px;max-height:800px;" align="center">
</p>

<p style="text-align:center">
<img src="/teaching/CS472/Timetable/GPT/use-case-2-example-3-2.png" alt="ShareChatGPTConversations" style="max-width:550px;max-height:550px;" align="center">
</p>

The link to the Git Diff file and conversation with ChatGPT is provided below:
- Git Diff file: [Here](https://github.com/faker-js/faker/pull/2405/files#diff-1918769d4ce5178c72d08b74f069e98856eeddcb0391e5c39636c8c33051f7f9)
- ChatGPT Link: [https://chat.openai.com/share/8cb16814-2855-4fbd-87e5-bde8ba349728](https://chat.openai.com/share/8cb16814-2855-4fbd-87e5-bde8ba349728)

## Patch Not Applied (PN)
### **Example 1: Adaptation and tailored solutions**
Recall that deals with Conceptual advice from ChatGPT adapted for customized solutions fitting unique project needs.
- [PR link](https://github.com/laravel-json-api/core/pull/12)
- [ChatGPT link](https://chatgpt.com/share/e9555822-4ffb-4845-8e40-0bc6cbbc658d)

#### Conversation Summary
* **Initial ChatGPT Suggestion:** The developer initially received a regex for ULID from ChatGPT: ```^[0-9A-HJKMNP-TV-Z]{26}$``` [ChatGPT link](https://chatgpt.com/share/e9555822-4ffb-4845-8e40-0bc6cbbc658d). This regex is technically correct in terms of the ULID format, as it matches a 26-character string using base32 encoding.
* **Reviewer's Suggestion:** The reviewer (`@lindyhopchris`) in the pull request (PR) pointed out that to maintain consistency, they should follow the regex used by Laravel's `whereUlid()` method for route constraints. This suggestion ensures uniformity across the codebase, aligning with how ULIDs are handled in the Laravel framework.

The Laravel framework’s regex for ULIDs (in the link provided by the reviewer) is: [links](https://github.com/laravel/framework/blob/53b02b3c1d926c095cccca06883a35a5c6729773/src/Illuminate/Routing/CreatesRegularExpressionRouteConstraints.php#L48) are below:
```regex
[0-7][0-9a-hjkmnp-tv-zA-HJKMNP-TV-Z]{25}
```
This regex is slightly more specific than the one suggested by ChatGPT. It specifies that the first character should be a digit between 0-7, while the subsequent 25 characters can include both uppercase and lowercase letters from the ULID base32 set.

* **PR author's Acceptance:** The PR author (@Ashk2a) acknowledges the suggestion by stating, "*good idea to check Laravel directly!*" and proceeds to change their code to reflect the Laravel-style regex, which was confirmed in the code (File [MatchedIDs.php](https://github.com/laravel-json-api/core/pull/12/files)) with:
```php
public function ulid(): self
{
        return $this->matchAs('[0-7][0-9a-hjkmnp-tv-zA-HJKMNP-TV-Z]{25}');
}
```

#### Conclusion
This pull request demonstrates how the developer adapted ChatGPT’s suggested regex to meet the specific requirements of the project. 
The task falls under **code generation**, where ChatGPT was used to automatically generate a regex from a natural language prompt, and **code customization**, as the developer further modified the generated code to align with project standards and feedback. 
This aligns with the theme of **adaptation to project needs**, where conceptual advice from ChatGPT was tailored to ensure consistency with Laravel’s framework.

### **Example 2: Methodological Guidance**
Recall that in this theme ChatGPT's advice informs approaches or refined solutions, not directly applied as patches. The focus is on the broader approach or strategy influenced by ChatGPT

* [PR link](https://github.com/darklang/dark/pull/5063)
* [ChatGPT Link](https://chat.openai.com/share/2a6f10f0-d45d-4e71-ac57-584570baeda8)

The developer's interaction with ChatGPT in the pull request shows a clear progression from a more complex approach to a simpler, more efficient one. Let's break it down step by step:

#### **Initial Code (Before ChatGPT's Suggestion)**

<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/PN-EX-2.png" alt="ShareChatGPTConversations" style="max-width:710px;max-height:355px;" align="center"></p>

In this initial code, the developer is converting a `char` to its Unicode (UTF-32) code point using `System.Char.ConvertToUtf32`. 
This method works but is more suitable for handling UTF-16 surrogate pairs rather than single char values (which is likely overkill for the use case). 
The method is useful if you're dealing with surrogate pairs, but for ASCII or basic Unicode characters, it's unnecessary.

The reviewer (@pbiggar), after consulting ChatGPT, pointed out that using (int)c could achieve the same result in a simpler and more efficient way.
Goes ahead to state that ChatGPT suggested casting the `char` to an `int`, which would return the Unicode (or ASCII) code point for the character, and for most simple characters, this works perfectly.

#### **Refined Code (After ChatGPT’s Suggestion)**
The refined code can be gotten in the file [backend/src/BuiltinExecution/Libs/Char.fs](https://github.com/darklang/dark/pull/5063/files#diff-2949d723a79b066aa811f68b3bc6f1aa712cf44b63c8210febd62378a408c536)
<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/PN-EX-2-2.png" alt="ShareChatGPTConversations" style="max-width:916px;max-height:200px;" align="center"></p>

In the updated version:
* **Simplified Conversion:** The developer replaced `System.Char.ConvertToUtf32` with `int c.[0]`, which is a much simpler and direct way to get the integer (ASCII/Unicode) value of a character.
* Added Validation: The code now includes additional logic:
  * Check if the character is a digit: `System.Char.IsDigit(c[0])`.
  * Range validation: The charValue is checked to see if it's in the range `[0, 256)`, likely to ensure it's within the ASCII range.
  * Conditional Handling: If the charValue is valid (within the range), it returns an optional integer (`Dval.optionSome (DInt charValue)`), otherwise it returns `Dval.optionNone`.

#### Conclusion
The developer's interaction with ChatGPT falls under the methodological guidance theme, where ChatGPT's advice helped refine the developer's approach rather than being directly applied as a patch. 
This guidance is explicitly connected to program repair as it involved identifying and fixing inefficiencies in the initial code, simplifying the solution based on ChatGPT’s recommendation. 
Additionally, it relates to code generation because ChatGPT suggested an alternative method to generate the correct code, enabling the developer to implement a more efficient solution. 
In both cases, ChatGPT informed the process of improving the code, aligning with these software engineering tasks.


## None Existing Patch (NE)
### **Example 1: Conceptual Guidance & Theoretical Advice**
In this example ChatGPT does not recommend specific patches. Instead, the discussions revolve around broader programming concepts and design principles. These conversations aim to enhance code readability and maintainability by focusing on theoretical advice and best practices, rather than direct code implementations. 

The details of PR and ChatGPT conversation links are below:

- PR: [https://github.com/codecrafters-io/frontend/pull/1061](https://github.com/codecrafters-io/frontend/pull/1061)
- ChatGPT Link: [https://chat.openai.com/share/d668d64c-182e-4e9d-8e17-6517d91fc65e](https://chat.openai.com/share/d668d64c-182e-4e9d-8e17-6517d91fc65e) 

The reviewer used ChatGPT to critique poor naming conventions, stating: ```"Bad naming,
this should be something like selectedPricingFrequency. Reasoning: [chatgpt link]"```. In response, the PR author acknowledged the need for improvement: ```"[...] we don’t seem to be getting better with naming [..], talk to ChatGPT about it, [...] we need to pay extra attention to it"```. 

<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/ne-example.png" alt="ShareChatGPTConversations" style="max-width:700px;max-height:700px;" align="center"></p>

In this case, a code snippet was not necessary because the discussion focused on best practices for **naming variables** rather than on specific feature implementation or bug fixes. The interaction was primarily conceptual, aimed at improving code quality.

Developers can benefit from using AI tools like ChatGPT to refine and elevate their **coding standards**, particularly in areas like naming conventions which significantly impact code readability
and maintainability. In addition, learning and self-review practices should be encouraged within development teams, using AI as a tool to provide immediate feedback and suggestions on how to improve code quality and adhere to best practices. 

### **Example 2: Debugging and Optimization Strategies**
This example showcase how developers utilize ChatGPT for debugging, performance optimization and refining algorithms. The details of PR and ChatGPT conversation links are below:

- PR: [https://github.com/darklang/dark/pull/5068](https://github.com/darklang/dark/pull/5068)
- ChatGPT Link: [https://chat.openai.com/share/7fe27ca4-5c0e-431b-953b-7f6e23710b5c](https://chat.openai.com/share/7fe27ca4-5c0e-431b-953b-7f6e23710b5c) 

<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/ne-example-2.png" alt="ShareChatGPTConversations" style="max-width:700px;max-height:700px;" align="center"></p>

The PR reviewer requested an alternative method to optimize performance issues, recalling, ```"I remember you mentioning that the performance of pushback isn’t great. Do you recommend a different approach"```. In response, the PR author employed ChatGPT to evaluate code performance and investigate other optimization strategies. After reviewing ChatGPT’s recommendations, the author suggested a new approach: ```"[...] appending it to the front and then reversing should do it [...]"```. The discussion did not yield a specific
code snippet because ChatGPT offered a strategy for optimization rather than a direct coding solution.

Developers can leverage AI tools to obtain high-level recommendations for code optimization, allowing them to rethink and refine their implementations based on AI-generated insights, which can lead to more efficient solutions.

## Getting Started With ChatGPT

To begin using ChatGPT (if you haven't already), simply go to [https://chat.openai.com/](https://chat.openai.com/) and create a free account. For this class, the free ChatGPT 3.5 is sufficient.

To effectively use ChatGPT, you should provide it a good "prompt". The concept of ``Prompt Engineering`` is detailed in this research paper: [A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT](https://arxiv.org/abs/2302.11382).


Sharing Your ChatGPT Conversations on GitHub
====
Sharing ChatGPT conversations with other developers can be beneficial for several reasons:

- Collaborative problem-solving
- Learning and Knowledge Sharing
- Code Review and Improvement
- Getting Diverse Perspectives
- Best Practices and Tips
- Avoiding Pitfalls
- Building a Supportive Community
- Ethical Considerations
- Innovation and Exploration

1. Once you are ready to share your conversations, following the screenshots below to generate and copy a 
URL/Link. **Note: Don't worry, your personal profile will NOT be visible after the conversation link is generated, 
it will be automatically changed to ```Anonymous```**.

   <p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/share1.png" alt="ShareChatGPTConversations" style="max-width:700px;max-height:700px;" align="center"></p>

   <p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/share2.png" alt="ShareChatGPTConversations" style="max-width:500px;height:500px;" align="center"></p>

2. After copying the link, there are many places on GitHub where you can share your conversation (e.g., inside a PR, Issue, or Commit message).
For example, if you used ChatGPT to help you solve a bug, it would be better to add 
the link in the `PR` description or `PR` review comment. See the below:
   - Adding your conversation link in PR description
    
    <p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/share-review-1.png" alt="ShareChatGPTConversations" style="max-width:800px;max-height:800px;" class="center"></p>

   - Adding your conversation link during PR review activity
    
    <p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/share-review-2.png" alt="ShareChatGPTConversations" style="max-width:600px;max-height:600px;" class="center"></p>

# Lab Tasks:

## Task 1: Familiarizing with ChatGPT
1. Read the provided overview of ChatGPT in software engineering.
2. Explore the provided use cases and review the associated PRs and ChatGPT conversations.
3. Identify the different ways developers incorporate ChatGPT into their workflow.
4. Understand the tasks addressed in each use case and the outcomes achieved.

## Task 2: Hands-on with ChatGPT
In **Task 2.1, 2.2 & 2.3** below, you will continue working on the **team repo** where you submitted your previous lab tasks.
You will engage in practical exercises leveraging ChatGPT to enhance code quality, documentation, and understanding.

* **Organizational Guidelines**: Ensure your team repository remains organized by discussing appropriate folder names for each task and clearly documenting them in the report. Additionally, add unique identifiers, such as your names, to filenames to avoid potential conflicts. **For example**: In Task 2.1 below you could choose to name your file `yournames_<whatever code snippet name you want>`.
* **Pull Request Process**: Familiarize yourself with the steps involved in opening a pull request on your team repository. Instructions for this are intentionally omitted, encouraging independent problem-solving and skill development.
* **Verification and Collaboration**: Each task involves initiating a pull request with the code snippet requiring modification. After incorporating ChatGPT suggestions, update the pull request accordingly. Thoroughly verify suggestions to prevent potential issues, ensuring adherence to best practices, readability, and functionality. Test the code with diverse inputs and seek peer feedback to independently verify improvements.

Task 2.1: Code Refactoring
====
**Objective**:

Refactor a code snippet using ChatGPT to improve code quality and readability.

**Instructions**:
1. **Select a Code Snippet and Create an Issue**: Choose a code snippet in any programming language from your projects, an open-source repository, or Stack Overflow that exhibits duplication issues or could benefit from refactoring. Open an issue on the team repository describing the code snippet you've identified, the specific areas requiring improvement, and your goals for refactoring it. 
2. **Open a Pull Request**: Once the issue is created, open a pull request on the team repository with the identified code snippet and initiate the refactoring process. Provide a detailed description of the pull request, referencing the issue created in the previous step to provide context for the code snippet. In the description of the pull request, include a reference to the issue using one of the following keywords followed by the issue number: Closes #123, Fixes #123, Resolves #123.
  * For example, if the issue number is 123, you can write Closes #123 in the pull request description. This ensures proper tracking and closing of the issue when the pull request is merged.
3. **Task ChatGPT**: Engage with ChatGPT to seek advice on how to refactor the chosen code snippet. Provide ChatGPT with a brief description of the code's purpose and the specific areas you believe require improvement.
4. **Implement Refactorings**: Based on the suggestions provided by ChatGPT, implement the necessary refactorings to improve the quality and readability of the code. Ensure that the functionality of the code remains intact after refactoring.
5. **Update the Pull Request**: After implementing the refactorings, update the pull request to showcase the changes made to the code. Include a summary of the refactorings and any insights gained from the ChatGPT conversation inside the pull request's comment section. Also include the ChatGPT link of your conversations. This documentation aids in understanding the rationale behind the changes made and serves as a reference for future discussions or code reviews.
6. **Merge Pull Request**: Once the refactorings are implemented and reviewed, merge the pull request into the main repository. 

Example:

```python
# Original Code Snippet
def calculate_circle_area(radius):
    area = 3.14 * radius * radius
    return area

def calculate_rectangle_area(length, width):
    area = length * width
    return area

def calculate_triangle_area(base, height):
    area = 0.5 * base * height
    return area

# Refactored Code Snippet
import math

def calculate_circle_area(radius):
    return math.pi * radius ** 2

def calculate_rectangle_area(length, width):
    return length * width

def calculate_triangle_area(base, height):
    return 0.5 * base * height
```

Notes:
* In this example, the original code snippet contains duplication in the calculation of areas for different shapes (circle, rectangle, triangle).
* ChatGPT could provide suggestions on using built-in functions or libraries to simplify the calculations and eliminate redundancy.
* The refactored code snippet improves readability by using the `math` module for accurate calculations and removing unnecessary variables.
* Ensure to document the changes made and the rationale behind each refactoring in the GitHub pull request description.

Task 2.2: Documentation Assistance
====

**Objective**:

Create user-friendly and concise documentation for your code snippet using insights from ChatGPT.

**Instructions**:
1. **Select a Code Snippet and Create an Issue**: Choose a code snippet in any programming language from your own projects, previous classes, an open-source repository, or Stack Overflow. Open an issue on the team repository, providing a clear description of the code's purpose. Assign the issue to yourself to take ownership of the task. This step allows for collaboration and ensures transparency within the team.
2. **Open a Pull Request**: Once the issue is created, open a pull request on the team repository with the identified code snippet. Provide a comprehensive description of the pull request, referencing the issue created in the previous step to provide context for the code snippet. In the description of the pull request, include a reference to the issue using one of the following keywords followed by the issue number: Closes #123, Fixes #123, Resolves #123. 
3. **Engage with ChatGPT**: Interact with ChatGPT to seek advice on how to improve the documentation for the chosen code snippet. Provide ChatGPT with context regarding the code's functionality, any specific areas where the documentation is lacking or unclear, and your goals for enhancing it. Consider discussing potential improvements in organization, clarity, completeness, and language style.
4. **Implement Documentation Enhancements**: Based on the suggestions provided by ChatGPT, implement the necessary enhancements to the documentation to improve its clarity, completeness, and effectiveness. Focus on addressing any identified gaps, clarifying complex concepts, and ensuring that the documentation aligns with best practices and standards. 
5. **Update the Pull Request**: After implementing the documentation enhancements, update the pull request to reflect these changes. Include a summary of the changes made and insights gained from the ChatGPT conversation regarding the documentation improvements inside the pull request's comment section. Also include the ChatGPT link of your conversations. Request feedback from team members and iterate on the changes as necessary to achieve consensus and maintain documentation quality.
6. **Merge Pull Request**: Once the documentation enhancements are implemented and reviewed, merge the pull request into the main repository. 

**Example**:

```python
# Original Script: fibonacci_sequence.py
def fibonacci_sequence(n):
    sequence = [0, 1]
    for i in range(2, n):
        next_term = sequence[-1] + sequence[-2]
        sequence.append(next_term)
    return sequence

def main():
    n = 10
    sequence = fibonacci_sequence(n)
    print(f"The Fibonacci sequence up to {n} terms is: {sequence}")

if __name__ == "__main__":
    main()

# Documented Script: fibonacci_sequence.py
def fibonacci_sequence(n):
    """
    Generate a Fibonacci sequence up to the nth term.
    Args:
        n (int): The number of terms in the Fibonacci sequence to generate.
    Returns:
        list: A list containing the Fibonacci sequence up to the nth term.
    """
    sequence = [0, 1]
    for i in range(2, n):
        next_term = sequence[-1] + sequence[-2]
        sequence.append(next_term)
    return sequence

def main():
    """
    Main function to demonstrate the usage of the fibonacci_sequence function.
    """
    n = 10
    sequence = fibonacci_sequence(n)
    print(f"The Fibonacci sequence up to {n} terms is: {sequence}")

if __name__ == "__main__":
    main()
```
**Notes**:
* In this example, the original code snippet `fibonacci_sequence.py` lacks comprehensive documentation, making it unclear what the function `fibonacci_sequence` does and how to use it.
* Without proper documentation, it may be challenging for other developers to understand the purpose of the function and its intended usage.
* Adding documentation to describe the functionality, input parameters, return value, and any other relevant details would enhance the clarity and usability of the code.
* Clear and concise documentation is essential for facilitating collaboration and ensuring that code is maintainable and understandable by others.

Task 2.3: Understanding Complex Code
====

**Objective**:

Gain insights and understanding of complex code segments using ChatGPT to facilitate code comprehension and improvement.

**Instructions**:
1. **Select a Code Segment and Create an Issue**: Choose a complex code segment in any programming language from your projects, an open-source repository, or Stack Overflow. The code segment should be non-trivial and may involve intricate logic or algorithms. Open an issue on the team repository describing the complex code segment you've identified, the challenges you're facing in understanding or optimizing it, and the desired outcome (e.g., optimization, clarity). Provide a clear description of the code's purpose, any specific areas of confusion, and the desired outcome. This issue will serve as the context for the code segment. After creating the issue, copy the issue URL.
2. **Open a Pull Request**: After creating the issue, open a pull request on the team repository with the identified code snippet and initiate the refactoring process. Provide a comprehensive description of the pull request, referencing the issue created in the previous step to provide context for the code segment. In the description of the pull request, include a reference to the issue using one of the following keywords followed by the issue number: Closes #123, Fixes #123, Resolves #123. For example, if the issue number is 123, you can write Closes #123 in the pull request description. This ensures proper tracking and closing of the issue when the pull request is merged.
3. **Engage with ChatGPT and Apply Insights**: Interact with ChatGPT to seek insights and recommendations for understanding or improving the selected code segment. Provide ChatGPT with details from the issue, including the code segment's purpose, challenges, and desired outcome. Utilize the insights and recommendations provided by ChatGPT to gain a deeper understanding of the code segment and apply any suggested alternative approaches, optimizations, or simplifications to enhance the code's readability, performance, or maintainability.
4. **Code Enhancement**: Implement any recommended changes or improvements based on the insights gained from ChatGPT. Refactor the code segment to incorporate the suggested optimizations, clarify complex logic, or address identified issues.
5. **Update the Pull Request**: After making the necessary enhancements or improvements to the code snippet, update the pull request to reflect these changes. Include a summary of the changes made and any insights gained from the ChatGPT conversation inside the pull request's comment section. Also include the ChatGPT link of your conversations. This documentation aids in understanding the rationale behind the changes made and serves as a reference for future discussions or code reviews.
6. **Merge Pull Request**: Once the refactorings and enhancements are implemented and reviewed, merge the pull request into the main repository. 

**Example**:

<!--div style="text-align:center;">
    <img src="task2.3.png" alt="Code Snippet" style="max-width:600px;max-height:600px;">
</div-->

```python
# Original Code Snippet: Complex Operation
def complex_operation(number):
    """
    Perform a complex mathematical operation on the input number.
    Args:
        number (int): The input number.
    Returns:
        int: The result of the complex operation.
    """
    return number ** 2 + number ** 3

# Updated Code Snippet: Simplified Operation
def simplified_operation(number):
    """
    Perform a simplified mathematical operation on the input number.
    Args:
        number (int): The input number.
    Returns:
        int: The result of the simplified operation.
    """
    result = number * number  # Square the number
    result += number * number * number  # Cube the number and add to the result
    return result
```

**Notes**:
* In this example, the original function `some_complex_operation(data_point)` represents a complex algorithmic operation that may be difficult to understand or optimize.
* ChatGPT could provide insights on potential simplifications, alternative algorithms, or optimizations to enhance the function's readability or performance.
* The simplified function `simplified_operation(data_point)` demonstrates how the algorithmic complexity can be reduced while achieving the same functionality.
* Ensure to thoroughly test the simplified function to validate its correctness and efficiency before integrating it into the project.

Task 2.4: Workflow Automation with GitHub Actions (Continuation from CI Lab)
====
In this task, you will continue building the Continuous Integration (CI) pipeline initiated in the previous lab on **Testing and CI**. All the code will be implemented in you individual **CI Lab** Repo (or fork).

**Objective:**

Automate workflow tasks using GitHub Actions to enhance efficiency and streamline development processes.

**Instructions:**

1. **Review Previous Workflow**: Review the CI workflow created in the previous lab (Task 2). Understand the structure of the workflow file (`workflow.yml`) and the sequence of steps defined to build, test, and validate the application code.

2. **Enhance Workflow with Additional Automation:** Identify areas within the CI workflow where additional automation can be beneficial. This may include steps for code analysis, documentation generation, or deployment preparations.
Consider incorporating tasks that leverage external tools or services, such as code quality analysis tools, static code analysis, or vulnerability scanning services.

3. **Engage with ChatGPT for Workflow Optimization:** Discuss potential enhancements or optimizations for the CI workflow with ChatGPT. Describe the current workflow structure, any bottlenecks or inefficiencies, and the desired outcome of automation improvements. Seek recommendations on best practices for integrating additional automation steps, ensuring compatibility with existing workflow components, and maximizing workflow performance.
4. **Implement ChatGPT Recommendations**: Based on the insights and recommendations provided by ChatGPT, update the workflow file (`workflow.yml`) to incorporate the suggested automation improvements.
Modify the existing workflow steps or add new steps as necessary to integrate the recommended automation tasks seamlessly into the CI pipeline.

5. **Testing**: Test the modified CI workflow to ensure that the new automation tasks function as expected and do not introduce regressions.

**Example:** 

```angular2html
name: CI workflow
on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main
jobs:
  build:
    runs-on: ubuntu-latest
    container: python:3.9-slim
    steps:
      - name: Checkout
        uses: actions/checkout@v3
      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt
      - name: Lint with Flake8
        run: |
          flake8 src --count --select=E9,F63,F7,F82 --show-source --statistics
          flake8 src --count --max-complexity=10 --max-line-length=127 --statistics
      - name: Run unit tests with nose
        run: nosetests -v --with-spec --spec-color --with-coverage --cover-package=src
      - name: SonarQube analysis
        run: |
          # Replace <SONAR_TOKEN> and <SONAR_PROJECT_KEY> with your SonarQube token and project key
          sonar-scanner \
            -Dsonar.projectKey=<SONAR_PROJECT_KEY> \
            -Dsonar.sources=src \
            -Dsonar.host.url=<SONARQUBE_URL> \
            -Dsonar.login=<SONAR_TOKEN>
```
Notes:
- In this example, the CI workflow file `workflow.yml` is enhanced with additional automation steps based on recommendations from ChatGPT.
- This modification adds a step named "SonarQube analysis" that runs SonarScanner to analyze the src directory of your project and sends the results to the SonarQube server for evaluation.
- ChatGPT recommendations may include suggestions for integrating third-party tools or services, optimizing workflow performance, or ensuring code quality and security.
- Regularly review and update the CI workflow based on feedback from ChatGPT, changes in project requirements, or advancements in CI/CD best practices.

# Task 3: Reflection Report

**Objective**:
Reflect on your experience with ChatGPT in completing the hands-on tasks and its impact on your understanding of software engineering practices.

Instructions:
Write a reflection report discussing your experience with ChatGPT during the completion of the lab tasks outlined below:

* Task 1: Familiarizing with ChatGPT
* Task 2.1: Code Refactoring
* Task 2.2: Documentation Assistance
* Task 2.3: Understanding Complex Code
* Task 2.4: Workflow Automation with GitHub Actions

In your reflection, address the following points:
1. *Initial Impressions*: Describe your initial expectations and impressions of using ChatGPT for software engineering tasks.
2. *Task Experiences*: Reflect on your experiences with each task, including any challenges faced, insights gained, and lessons learned. Provide concrete examples by linking to relevant pull requests or the CI pipeline for Task 2.4.
3. *Impact*: Discuss how ChatGPT has impacted your approach to software development, collaboration with teammates, and problem-solving skills.
4. *Lessons Learned*: Summarize the key lessons you've learned from working with ChatGPT and how they may influence your future projects.
5. *Future Applications*: Explore potential applications of ChatGPT in your future software development projects or other areas of interest.

**Format**: Your reflection report should be structured as a brief document with the following sections:

* **Title**: Reflection Report on ChatGPT Usage
* **Introduction**: Brief overview of the purpose and structure of the reflection report.
* **Task Experiences**: Concise reflection on each task, highlighting challenges, insights, and lessons learned. Include hyperlinks to relevant pull requests or the CI pipeline for Task 2.4 to provide concrete examples of your work and experiences with ChatGPT. **(1-2 paragraphs per task)**
* **Impact**: Discussion on the overall impact of ChatGPT on your software development process and skills. **(1-2 paragraphs)**
* **Lessons Learned**: Summary of key lessons learned from working with ChatGPT and their implications for future projects. **(1-2 paragraphs)**
* **Future Applications**: Exploration of potential future applications of ChatGPT in software development or related fields. **(1-2 paragraphs)**
* **Conclusion**: Closing remarks summarizing your reflections on using ChatGPT in software engineering tasks.

**Submission**:
Submit your reflection report on Web Campus.

**Note**: The reflection report should be concise and focused, providing insights into your experience with ChatGPT without requiring extensive elaboration. Aim to capture the key points and lessons learned from each task, as well as your overall impressions and future outlook.

# Conclusion
In this lab, you learned about the various ways developers utilize ChatGPT in software engineering tasks. Through hands-on tasks, you practiced leveraging ChatGPT for code refactoring, documentation assistance, workflow automation, and code understanding. These skills will be valuable as you embark on collaborative software development team projects. While the lab has introduced you to how developers seek solutions from ChatGPT for a limited set of software engineering tasks, it's important to note that in your project work, you will experiment with a broader range of software engineering tasks. For a deeper understanding of these tasks, refer to **Section 6** of the paper, Hou at al. [LLMs for SE: A SLR](https://arxiv.org/pdf/2308.10620.pdf)