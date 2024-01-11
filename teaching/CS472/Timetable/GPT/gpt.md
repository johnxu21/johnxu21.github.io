---
layout: page
title: CS472 - CHAT GPT - Tutorial
permalink: /teaching/CS472-Spring2023/Timetable/GPT/
---
In this lab, you will learn how to leverage ChatGPT for software development task. You will also learn various ways of sharing you conversation to support collaborative software engineering.

Overview
=======
ChatGPT is a language model developed by OpenAI. It is part of the GPT (Generative Pre-trained Transformer) family of models, specifically GPT-3.5-turbo. GPT-3.5-turbo is a highly advanced language model that is designed to understand and generate human-like text based on the input it receives.


### How is ChatGPT being used in Software Engineering?
ChatGPT is being used in various ways in the field of software engineering. Its natural language understanding and generation capabilities make it a valuable tool for developers, both for individual tasks and collaborative projects. Here are some ways ChatGPT is applied in software engineering:

1. Code Generation and Completion
2. Programming Assistance
3. Learning and Education
4. Documentation and Technical Writing
5. Code Reviews
6. Prototyping and Idea Exploration
7. Natural Language Interfaces
8. Task Automation
9. Bug Reporting and Issue Tracking:

To begin using ChatGPT (if you haven't already), simply go to https://chat.openai.com/ and create a free account. For this class, the free ChatGPT 3.5 is sufficient.

Task 1 - Example of Code Generation and Optimization using ChatGPT
=======
To effectivity use ChatGPT you should provide it a good "prompt". The concept of ``Prompt Engineering`` is detailed in this research paper: [A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT](https://arxiv.org/abs/2302.11382).
1. Let us ChatGPT to generate the code for this LeetCode problem  ```Two Sum```: https://leetcode.com/problems/two-sum/description/
   * **Simple prompt:** Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`
  
   ```python
    def two_sum(nums, target):
    # Create a dictionary to store the indices of elements
    num_indices = {}

    # Iterate through the array
    for i, num in enumerate(nums):
        # Calculate the complement needed to reach the target
        complement = target - num

        # Check if the complement is in the dictionary
        if complement in num_indices:
            # If found, return the indices of the two numbers
            return [num_indices[complement], i]

        # Otherwise, store the current element's index in the dictionary
        num_indices[num] = i

    # If no solution is found, return an empty list or raise an exception
    # (depending on the problem requirements)
    return []
   ```
   * Let us give ChatGPT more information:
    -  **Prompt:** Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target. You may assume that each input would have exactly one solution, and you may not use the same element twice. You can return the answer in any order.
    ```python
    def two_sum(nums, target):
        # Create a dictionary to store the indices of elements
        num_indices = {}

        # Iterate through the array
        for i, num in enumerate(nums):
            # Calculate the complement needed to reach the target
            complement = target - num

            # Check if the complement is in the dictionary
            if complement in num_indices:
                # If found, return the indices of the two numbers
                return [num_indices[complement], i]

            # Otherwise, store the current element's index in the dictionary
            num_indices[num] = i

        # No need to handle the case when no solution is found, as the problem
        # states that there is exactly one solution.

    ```
  You can continue refining the prompt in order to get a more precise and optimized solution. See the full conversation here: https://chat.openai.com/share/5ed4faed-52c3-45dd-9c6a-1363b3f0dd91

2. In this second part of task 1, try to use ChatGPT any task of your choice. Observe how designing and refining prompts can help you achieve your goal.
   - Are you able to get your solution?
   - How long did you take to get your answer?
   - What prompting pattern (s) did you adopt? 

Task 2: Sharing Your ChatGPT Conversations on GitHub
====
In this task I will show you how to share you ChatGPT conversations with fellow developers. Sharing ChatGPT conversations with other developers can be beneficial for several reasons:

- Collaborative Problem Solving:
- Learning and Knowledge Sharing:
- Code Review and Improvement:
- Getting Diverse Perspectives:
- Best Practices and Tips:
- Avoiding Pitfalls:
- Building a Supportive Community:
- Ethical Considerations
- Innovation and Exploration:

1. Once you are ready to share your converstions, following the screenshots below to generate and copy a URL/Link. NB: Don't worry, your details will NOT be visible after the conversation link is generated, it will be automatically changed to "Anonymous".

   <img src="/teaching/CS472/Timetable/GPT/share1.jpeg" alt="ShareChatGPTConversations" style="width:612px;height:114px;" align="center">

   <img src="/teaching/CS472/Timetable/GPT/share2.jpeg" alt="ShareChatGPTConversations" style="width:612px;height:114px;" align="center">

2. After copying the link, there are many places on GitHub where you can share you conversation depending on the activity you are doing. For example, if you used ChatGPT to help you solve a bug, it would be better to add the link in the `PR` description. See the below:
   - Adding your conversation link in PR description
    
    <img src="/teaching/CS472/Timetable/GPT/share-review-1.jpeg" alt="ShareChatGPTConversations" style="width:612px;height:114px;" align="center">

   - Adding your conversation link during PR review activity
    
    <img src="/teaching/CS472/Timetable/GPT/share-review-1.jpeg" alt="ShareChatGPTConversations" style="width:612px;height:114px;" align="center">

