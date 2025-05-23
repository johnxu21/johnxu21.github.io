---
layout: page
title: CS472 - Using GenAI tools in Software Engineering Tasks - Lab
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

# **This individual assignment is due Feb 28th, 2025**

## **Important Note**  

While this lab may appear lengthy, most of the content is **informative** and includes **illustrations** to help you understand the tasks. It is designed to be easy to read and follow.  

### **Lab Structure & Grading**  
This lab consists of **two main tasks**:  
- **Task 1: Quiz (10 points)** – A short quiz to assess your understanding on how developers use GenAI to address some software development tasks.  
- **Task 2: Hands-On Activity (20 points)** – A practical exercise where you will apply what you learned.  

---

## **Introduction to ChatGPT in Software Engineering**
In this lab, you'll learn how to use **ChatGPT**, a language model developed by OpenAI, to tackle software engineering tasks. ChatGPT can generate human-like text based on input and has become a valuable tool for developers. You’ll explore how developers integrate ChatGPT into their workflow and how to use it responsibly to improve productivity.  

This lab builds on research presented at the [2024 International Conference on Automated Software Engineering (ASE)](ASE_Paper_2024.pdf), where we studied ChatGPT’s role in open-source projects. The insights from this research will help you understand ChatGPT’s impact on software engineering tasks and decision-making.  

---

## **ChatGPT’s Role in Software Engineering**
ChatGPT is widely used across the software development lifecycle, including:  

- **Requirements engineering** – Requirements classification, resolving ambiguity  
- **Software design** – GUI retrieval, rapid prototyping  
- **Development** – Code generation, search, documentation  
- **Quality assurance** – Test generation, bug detection  
- **Maintenance** – Code review, duplicate bug detection  
- **Management** – Effort estimation  

For an in-depth discussion, see **Section 6** of Hou et al. [LLMs for SE: A SLR](https://arxiv.org/pdf/2308.10620.pdf).  

---

## **Task 1: Exploring ChatGPT’s Role in Software Engineering**
Before moving to hands-on tasks, you’ll first review **real-world examples** of how developers use ChatGPT in software development.  

### **How Developers Use ChatGPT**
The following case studies illustrate three key scenarios where ChatGPT was used in GitHub pull requests:  

- **Patch Applied (PA)** – Code was directly integrated.  
- **Patch Not Applied (PN)** – Suggestions were modified or rejected.  
- **None Existing Patch (NE)** – ChatGPT provided guidance without direct code suggestions.  

Key themes include:
- **PN Themes**: Project adaptation, methodological guidance, specific functionality, technical limitations, and clarifications.  
- **NE Themes**: Conceptual guidance, documentation improvement, education, debugging, and optimization strategies.  

Each case includes **GitHub pull requests and developer interactions** to show ChatGPT’s impact.  

### **Your Task (10 points)**
1. **Read the Case Studies** carefully to understand how ChatGPT influenced decisions.  
2. **Take the WebCampus Quiz** (10 multiple-choice questions) to check your understanding before proceeding to hands-on exercises.  

---

# **Case Studies**  


## Patch Applied (PA)
In our lab research, we observe that developers integrate ChatGPT-generated patches at different levels based on project constraints such as maintainability, readability, and coding standards. Our findings indicate that a **median integration rate of 25%** suggests that most AI-generated patches are **only partially adopted**, rather than fully applied.

### **Boxplot of ChatGPT Patch Integration**
The figure below illustrates the distribution of ChatGPT-generated code integrated into pull requests.
A **boxplot analysis** of merged pull requests shows three categories of integration:

![ChatGPT Patch Integration in Pull Requests Boxplot](boxplot.jpg)

1. **Low (0–25%)** – Only minor elements were used, with significant modifications.
2. **Moderate (25–75%)** – Some parts were integrated, but developers refined the patch to fit project needs.
3. **High (75–100%)** – The AI-generated patch was largely accepted with minimal changes.

This data highlights that **ChatGPT serves as a starting point**, but developers still refine AI-suggested code before merging it into real-world projects.

Now that we understand the varying levels of ChatGPT patch integration, let’s look at real-world **examples where AI-generated patches were applied** in GitHub pull requests.

### **Example 1: Code Duplication and Refactoring**

- [PR link](https://github.com/nbd-wtf/nostr-tools/pull/241)
- [ChatGPT Link](https://chat.openai.com/share/f09f38e5-f541-4f98-9483-e183f5650398)

A developer used ChatGPT during the `Software maintenance` task of `code duplication and refactoring` in the `nostr-tools` project. The developer aimed to resolve code repetition and refactor the code.

The pull request shows code changes to address **duplication issues**, improving code quality. Code duplication often leads to maintenance challenges, bugs, and reduced readability. By using ChatGPT, the developer sought guidance to efficiently refactor the code.

**Developer Prompt:**
```text
I have some duplication in my TypeScript code. I want to resolve it by creating a discriminated union based on the keys and values of the interface. Is this possible?
```

<p align="center">
  <img src="/teaching/CS472/Timetable/GPT/example-1-1.png" alt="ChatGPTPrompt" style="max-width:700px; max-height:700px;">
</p>

**GitHub file diff:** [View here](https://github.com/nbd-wtf/nostr-tools/pull/241/files#diff-98476df5961449c9b87e4a05e4cf190b90d14815cb1b23f1e2d5398467287b61)

<p align="center">
  <img src="/teaching/CS472/Timetable/GPT/example-1-2.png" alt="FileDiff" style="max-width:1000px; max-height:1000px;">
</p>


### **Example 2: Deployment Documentation**

Links to PR and ChatGPT conversation:
- [PR Link](https://github.com/swarmion/swarmion/pull/678)
- **Note:** The original ChatGPT conversation link has been deleted by the developer. However, all the necessary details and context from the conversation are provided here for your reference. You can still follow along with the example using the information already included.

Documentation plays a key role in ensuring effective communication and collaboration in software development. It can take various forms such as:
- **Requirements Documentation**: Specifications (functional & non-functional).
- **Design Documentation**: System architecture, data flow.
- **Technical Documentation**: Code, APIs, algorithms, and data.
- **Testing & QA Documentation**: Test plans and quality assurance.
- **Deployment Documentation**: Guidelines for software deployment.

In this case, the developer used ChatGPT to generate user-friendly, concise deployment documentation for the `release.sh` script. 

**Developer's prompt:**
```plaintext
Act as a developer advocate with 5 years of experience. Write quick documentation for this `release.sh` script. Use bullet points and short sentences. Add emojis where needed.
```

<p style="text-align:center">
<img src="/teaching/CS472/Timetable/GPT/example-2-1.png" alt="ShareChatGPTConversations" style="max-width:550px;max-height:550px;border:1px solid black;" align="center">
</p>

<br />

As a result, the [`CONTRIBUTION.md`](https://github.com/swarmion/swarmion/pull/678/files#diff-eca12c0a30e25b4b46522ebf89465a03ba72a03f540796c979137931d8f92055) file was updated with documentation from ChatGPT to help new contributors get started.

<p style="text-align:center">
<img src="/teaching/CS472/Timetable/GPT/example-2-2.png" alt="ShareChatGPTConversations" style="max-width:550px;max-height:550px;" align="center">
</p>


### **Example 3: Configuring GitHub Actions Workflow**

- [PR link](https://github.com/faker-js/faker/pull/2405) - [Git Diff File](https://github.com/faker-js/faker/pull/2405/files#diff-1918769d4ce5178c72d08b74f069e98856eeddcb0391e5c39636c8c33051f7f9)
- [ChatGPT Conversation](https://chat.openai.com/share/8cb16814-2855-4fbd-87e5-bde8ba349728)

In Examples 1 and 2 above, the developer used the code generated by ChatGPT "as-is." However, this example demonstrates another use case where the developer integrates only a *portion* of the code snippet suggested by ChatGPT. The prompt provided by the developer aligns with the `Configuring GitHub Actions Workflow` task, which falls under the `Software Configuration Management (SCM)` activity. SCM encompasses version control, configuration management, and process management. Configuring GitHub Actions workflow specifically relates to automating the building, testing, and deploying of code changes, which aligns with CI practices.

In this case, after reviewing the GitHub link and ChatGPT conversation, we can see that the developer is seeking guidance on setting up and configuring `GitHub Actions workflows` for the `Faker.js` library. The GitHub link shows changes made to the `GitHub Actions workflow` configuration file.

**Developer Prompt 1:** 
```plaintext
Write a GitHub Action yml file that blocks the PR from merging when there is a label named "do NOT merge yet" or "s: on hold"
```

**Developer Prompt 2:**
```plaintext
How can I check "s: on hold" with "contains" using "github.event.pull_request.labels.*.name"
```
Below is the final code snippet generated by ChatGPT and the portion integrated into the GitHub pull request.

<p style="text-align:center">
<img src="/teaching/CS472/Timetable/GPT/use-case-2-example-3-1.png" alt="ShareChatGPTConversations" style="max-width:800px;max-height:800px;" align="center">
</p>

<p style="text-align:center">
<img src="/teaching/CS472/Timetable/GPT/use-case-2-example-3-2.png" alt="ShareChatGPTConversations" style="max-width:550px;max-height:550px;" align="center">
</p>

----

## **Patch Not Applied (PN)**

### **Example 1: Adaptation and Tailored Solutions**
This example shows how ChatGPT's conceptual advice was adapted for customized solutions to fit unique project needs.
- [PR link](https://github.com/laravel-json-api/core/pull/12)
- [ChatGPT link](https://chatgpt.com/share/e9555822-4ffb-4845-8e40-0bc6cbbc658d)

#### **Conversation Summary**
* **Initial ChatGPT Suggestion:** ChatGPT provided a regex for ULID: `^[0-9A-HJKMNP-TV-Z]{26}$` to match a 26-character string using base32 encoding.
* **Reviewer's Suggestion:** The reviewer (`@lindyhopchris`) recommended using Laravel's `whereUlid()` regex for consistency, aligning with how ULIDs are handled in the Laravel framework. 
The Laravel [regex](https://github.com/laravel/framework/blob/53b02b3c1d926c095cccca06883a35a5c6729773/src/Illuminate/Routing/CreatesRegularExpressionRouteConstraints.php#L48) provided by the reviewer is

    ```regex
    [0-7][0-9a-hjkmnp-tv-zA-HJKMNP-TV-Z]{25}
    ```

    This regex specifies that the first character is a digit between 0-7, followed by 25 base32 characters.

* **PR Author's Acceptance:** The author (@Ashk2a) acknowledged the feedback and updated the code (File [MatchedIDs.php](https://github.com/laravel-json-api/core/pull/12/files)) to reflect the Laravel-style regex:

    ```php
    public function ulid(): self
    {
        return $this->matchAs('[0-7][0-9a-hjkmnp-tv-zA-HJKMNP-TV-Z]{25}');
    }
    ```

#### **Conclusion**
This pull request demonstrates how the developer adapted ChatGPT’s suggested regex to meet the specific requirements of the project. The task falls under the Software Engineering activity of **code customization**, as the developer further modified the generated code to align with project standards and feedback. This aligns with the theme of **adaptation to project needs**, where conceptual advice from ChatGPT was tailored to ensure consistency with Laravel’s framework.


### **Example 2: Methodological Guidance**
This theme focuses on how **ChatGPT's advice informs approaches or refined solutions**, rather than being directly applied as patches. The emphasis is on broader strategies influenced by ChatGPT.

* [PR link](https://github.com/darklang/dark/pull/5063)
* [ChatGPT Link](https://chat.openai.com/share/2a6f10f0-d45d-4e71-ac57-584570baeda8)

The developer's interaction with ChatGPT in this pull request demonstrates a progression from a complex to a simpler, more efficient solution. Here's a breakdown:

#### **Initial Code (Before ChatGPT's Suggestion)**

<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/PN-EX-2.png" alt="ShareChatGPTConversations" style="max-width:710px;max-height:355px;" align="center"></p>

In the initial code, the developer uses `System.Char.ConvertToUtf32` to convert a `char` to its Unicode (UTF-32) code point. While effective, this method is mainly suited for handling UTF-16 surrogate pairs and is unnecessary for basic `char` values. It's an overly complex solution for ASCII or basic Unicode characters.

The reviewer (@pbiggar), after consulting ChatGPT, noted that casting the `char` to an `int` would achieve the same result in a simpler and more efficient way. **ChatGPT suggested casting `char` to `int`**, which directly returns the Unicode (or ASCII) code point for the character—perfect for most simple characters.

#### **Refined Code (After ChatGPT’s Suggestion)**
The refined code can be found in the file [backend/src/BuiltinExecution/Libs/Char.fs](https://github.com/darklang/dark/pull/5063/files#diff-2949d723a79b066aa811f68b3bc6f1aa712cf44b63c8210febd62378a408c536).

<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/PN-EX-2-2.png" alt="ShareChatGPTConversations" style="max-width:800px;max-height:175px;" align="center"></p>

In the updated version:
* **Simplified Conversion**: The developer replaced `System.Char.ConvertToUtf32` with `int c.[0]`, which is a simpler and direct way to get the integer (ASCII/Unicode) value of a character.
* **Added Validation**: Additional logic was included to handle edge cases:
  * **Digit Check**: The code checks if the character is a digit using `System.Char.IsDigit(c[0])`.
  * **Range Validation**: It verifies that `charValue` is within the `[0, 256)` range, ensuring the value is within the ASCII range.
  * **Conditional Handling**: If `charValue` is valid, it returns `Dval.optionSome (DInt charValue)`, otherwise it returns `Dval.optionNone`.

#### **Conclusion**
The interaction in this pull request is a clear example of **methodological guidance**, where ChatGPT’s advice helps refine the developer's approach instead of being directly applied as a patch. This refinement aligns with the Software Engineering task of **program repair**, as it involved simplifying and improving the initial code to address inefficiencies.

By following ChatGPT's advice, the developer made the code more efficient and easier to maintain, demonstrating how **methodological guidance** can lead to better solutions in software engineering.

----

## None Existing Patch (NE)
### **Example 1: Conceptual Guidance & Theoretical Advice**
This theme emphasizes programming concepts, design principles, and optimization strategies, focusing on best practices for readability and maintainability without specific code implementations.

- [PR link](https://github.com/codecrafters-io/frontend/pull/1061)
- [ChatGPT Link](https://chat.openai.com/share/d668d64c-182e-4e9d-8e17-6517d91fc65e)

Let's break down the situation to understand how the developer changed their code based on the ChatGPT conversation:

#### **Original Problem**
<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/NE-EX-1-1.png" alt="ShareChatGPTConversations" style="max-width:800px;max-height:325px;" align="center"></p>

The developer was using the variable name `pricingFrequencyClicked`, which was problematic because the name implied an action (a click) rather than a state (the selected frequency). This didn't accurately reflect what the variable was being used for: to store the **selected pricing frequency** (e.g., 'monthly' or 'yearly').

#### **Developer's Implementation**
The final updates in the PR can be viewed in the file: [app/controllers/pay.js](https://github.com/codecrafters-io/frontend/pull/1061/files#diff-430dcbc461b77b60fd320d970946d870ed279a2952a06350872de59304e427e8).

<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/NE-EX-1-2.png" alt="ShareChatGPTConversations" style="max-width:800px;max-height:55px;" align="center"></p>

After the ChatGPT conversation, the developer renamed `pricingFrequencyClicked` to `selectedPricingFrequency`. This new name more accurately reflects that the variable holds the user's selection for pricing frequency, improving both readability and maintainability of the code.

#### **ChatGPT's Advice**
ChatGPT highlighted the issue with the variable name, explaining that `pricingFrequencyClicked` was not appropriate because it didn't align with the variable's purpose. It suggested using a name like `selectedPricingFrequency` to more accurately reflect that the variable holds a selection, not an action.

#### **Conclusion**
This interaction falls under the **"Conceptual Guidance & Theoretical Advice"** theme, where ChatGPT's recommendations helped improve the clarity and maintainability of the code by suggesting better naming conventions. This aligns with the software engineering tasks of **code review** and **code quality enhancement**, as it involved refining naming practices to enhance readability and maintainability.

In this case, ChatGPT played a key role in informing the process of improving code structure and long-term maintainability, aligning with these software engineering tasks.


### **Example 2: Debugging and Optimization Strategies**
This theme focuses on debugging methods, performance optimization, and refining algorithms, offering strategic insights into problem-solving approaches without providing specific code snippets.

- [PR link](https://github.com/darklang/dark/pull/5068)
- [ChatGPT Link](https://chat.openai.com/share/7fe27ca4-5c0e-431b-953b-7f6e23710b5c)

Let's break down how the developer improved their code based on a conversation with ChatGPT:

#### **Original Code**
<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/NE-EX-2-1.png" alt="ShareChatGPTConversations" style="max-width:895px;max-height:446px;" align="center"></p>

Initially, the developer was using `pushBack`, which appends an element to the end of a list. However, repeatedly using this operation can be inefficient, as it may require traversing the entire list, especially in larger datasets.

#### **ChatGPT's Advice**
After consulting ChatGPT, the developer received a suggestion to optimize the list operation by switching to `push` (which likely adds elements to the front of the list) and then reversing the list at the end. This approach is generally more efficient because adding to the front of the list is an O(1) operation in many functional languages, whereas `pushBack` can be an O(n) operation, where n is the length of the list.

#### **Updated Code**
The optimized code can be found in this PR file: [backend/testfiles/execution/stdlib/result.dark](https://github.com/darklang/dark/pull/5068/files#diff-ad820db3a141ba69514679a4698e3acb98c351faa8e2aaca9c3511c2740b8c19).

<p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/NE-EX-2-2.png" alt="ShareChatGPTConversations" style="max-width:676px;max-height:72px;" align="center"></p>

In this updated code:
- The developer switched to using `push` (adding to the front) and planned to reverse the list at the end.
- This new approach enhances performance, as adding to the front of the list is typically O(1), whereas using `pushBack` could result in O(n) complexity.

#### **Conclusion**
This interaction falls under the **Debugging & Optimization Strategies** theme, where ChatGPT provided advice to improve performance. Rather than directly offering a code solution, ChatGPT suggested a strategy—appending elements to the front of the list and reversing it later—to optimize performance. This aligns with the Software Engineering task of **performance optimization**, where the developer refined the algorithm based on ChatGPT's advice, ultimately enhancing the efficiency of the code.

ChatGPT played a key role in guiding the developer toward a more efficient solution for handling list operations, demonstrating how strategic advice can lead to performance improvements in software engineering.

# **Getting Started With ChatGPT**

To start using ChatGPT, go to [https://chat.openai.com/](https://chat.openai.com/) and create a free account. For this class, the free version of ChatGPT 3.5 is sufficient.

To make the most of ChatGPT, it’s important to provide well-structured prompts. The concept of **Prompt Engineering** is explored in this research paper: [A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT](https://arxiv.org/abs/2302.11382).

## Sharing Your ChatGPT Conversations on GitHub

Sharing your ChatGPT conversations with other developers can be highly beneficial for several reasons, such as:
- Collaborative problem-solving
- Learning and knowledge sharing
- Code review and improvement
- Gaining diverse perspectives
- Sharing best practices and tips
- Avoiding common pitfalls
- Building a supportive community
- Ethical considerations
- Innovation and exploration

### How to Share Your ChatGPT Conversations

1. **Generating a Shareable Link**:
   Once you're ready to share your ChatGPT conversation, follow the steps below to generate a shareable link. 
   **Note:** Your personal profile will be anonymized when the conversation link is generated.

   <p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/share1.png" alt="Generating a ChatGPT Share Link" style="max-width:700px;max-height:700px;" align="center"></p>

   <p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/share2.png" alt="Sharing ChatGPT Conversations" style="max-width:500px;max-height:500px;" align="center"></p>

2. **Sharing on GitHub**:
   After copying the link, you can include it in various places on GitHub, such as a pull request (PR), issue, or commit message. For instance, if ChatGPT helped you solve a bug, you could include the link in the PR description or during a PR review. See examples below:

   - **Adding the conversation link in a PR description**:

     <p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/share-review-1.png" alt="Adding ChatGPT Link to PR Description" style="max-width:800px;max-height:800px;" class="center"></p>

   - **Adding the conversation link during PR review**:

     <p style="text-align:center"><img src="/teaching/CS472/Timetable/GPT/share-review-2.png" alt="Adding ChatGPT Link during PR Review" style="max-width:600px;max-height:600px;" class="center"></p>

## Task 2: Hands-on with ChatGPT (20 points)

In **Task 2.1, 2.2, and 2.3**, you will work on your **team repository**, where previous lab tasks were submitted. You'll use ChatGPT to improve code quality, documentation, and comprehension.  

- The author **must** use ChatGPT during the development process.  
- Your goal is to enhance your code by applying ChatGPT's suggestions while ensuring correctness and maintainability.  

---

### **Organizational Guidelines**:

1. **Repository Structure**:  
   - To maintain consistency, **store your files inside the `gen_ai` directory**, with subfolders for each task. For example:
     ```bash
     gen_ai/task2.1/yourname_refactor_code.py
     gen_ai/task2.2/yourname_docstring_update.py
     ```
   - **Check if the directories already exist** before creating them. If another team member has already added them and merged their pull request, **pull the latest changes instead of recreating them** (see instructions below).

2. **Pull Requests (PRs)**:  
   - Open a **PR for each task** with clear descriptions, referencing ChatGPT suggestions.
   - **Example PR Title**:  
     > "Refactored function X using ChatGPT's recommendation."
   - **PR Description Example**:  
     > "Refactored the loop structure to improve efficiency. Suggested by ChatGPT [conversation link]."
     
---

### **Verification and Collaboration**:

1. **Ensuring Your Local Repository is Up-to-Date**:  
   Before making any modifications, **ensure you have the latest version** of the repository by running:

   ```bash
   git checkout main
   git fetch upstream  # Fetch the latest changes from the team repository (`upstream/main`) without merging yet.
   git merge upstream/main  # Merge the latest changes from the team repository into your local main branch.
   git push origin main  # Push the updated main branch to your fork.
   ```

## Task 2.1: Code Refactoring Using ChatGPT

**Objective**: Refactor a code snippet using ChatGPT to improve code quality and readability.

### **Instructions**:

1. **Select a Code Snippet:** Choose a code snippet from your current project, an open-source repository, or a past assignment from your previous programming classes. Open an issue on the team repository identifying specific problems (e.g., duplication, inefficiency, poor readability).
2. **Consult ChatGPT**: Ask ChatGPT for advice on how to refactor the code. Provide context on the code's purpose and areas needing improvement. Copy the link to the ChatGPT conversation.
3. **Open a Pull Request (PR)**: Submit a PR with the selected code snippet. Reference the issue created earlier (e.g., "Closes #123") and provide a summary of the refactoring goal in the PR description.
4. **Implement Refactorings**: Apply ChatGPT's suggestions to improve the code’s quality and readability. Ensure that the functionality of the code remains intact after refactoring.
5. **Merge PR**: Once your colleague has reviewed the PR and confirmed the improvements, you can merge the PR into the team repository.

## Task 2.2: Improving Documentation with ChatGPT

**Objective**: Use ChatGPT to enhance documentation for a selected code snippet.

### **Instructions**:

1. **Select a Code Snippet**: Choose a code snippet from your current project, an open-source repository, or a past assignment from your previous programming classes that lacks proper documentation. Open an issue on the team repository to take ownership of the task.
2. **Consult ChatGPT**: Ask ChatGPT to help generate clear and user-friendly documentation for the code. Provide relevant context about the code's functionality and any areas where the documentation is lacking.
3. **Open a Pull Request (PR)**: Submit a PR with the improved documentation to your team repository. Reference the issue using keywords like "Closes #123" or "Fixes #123."
4. **Update Documentation**: Based on ChatGPT’s suggestions, improve the code documentation to ensure it is clear, complete, and easy to understand.
5. **Merge PR**: After the review is completed and improvements are confirmed, merge the PR into the main branch of your team repository.

## Task 2.3: Understanding Complex Code with ChatGPT

**Objective**: Use ChatGPT to help comprehend and improve a complex code segment.

### **Instructions**:

1. **Select a Complex Code Segment**: Choose a complex code segment from your current projects, an open-source repository, or a past programming assignment. Open an issue on your team repository detailing the complexity and the challenges you're facing in understanding the code.
2. **Consult ChatGPT**: Provide ChatGPT with the code and highlight specific areas where you need clarity or improvements. Ask for suggestions on how to simplify, optimize, or improve the code.
3. **Open a Pull Request (PR)**: Submit a PR to your team repository with the selected code segment. Reference the issue you created and explain the goal of simplifying or optimizing the code in the PR description.
4. **Implement Changes**: Apply ChatGPT’s recommendations to simplify or optimize the code, ensuring that functionality is maintained.
5. **Merge PR**: Once the review is complete and all changes are confirmed, merge the PR into the team repository.

# **Task 3: Summary Report**
Write a brief report that includes:

**Task Summary**: 
   - For each task (Exploring ChatGPT's Role in Software Engineering, Code Refactoring, Documentation Assistance, Understanding Complex Code), provide a short description (1-2 sentences) of what you did.
   - Include the link to the individual pull request (PR) for each task.

### **Submission**:
- Submit your report on Web Campus.


