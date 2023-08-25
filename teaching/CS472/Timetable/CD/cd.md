---
layout: page
title: CS472 - CI - Building a Tekton Pipeline
permalink: /teaching/CS472-Spring2023/Timetable/CD/
---
In this lab, you will build Tekton pipeline.

Task 1 - Create a simple Tekton pipeline 
=======
1. Clone the code you need to test and change directory to ```wtecc-CICD_PracticeCode/labs/01_base_pipeline/```
   ```
    git clone https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git
   ```
   Navigate to the labs/01_base_pipeline folder. All of your work will be completed with the files in this folder.
2. There is starter code in the ```labs/01_base_pipeline``` folder for a task and a pipeline. Navigate and open the ```tasks.yaml``` file to edit it:
   ```yaml
    apiVersion: tekton.dev/v1beta1
    kind: Task
    metadata:
       name: <place-name-here>
    spec:
       steps:
   ```
   * The first thing you want to do is give the task a good name. Change ```<place-name-here>``` to ```hello-world```.
   * The next thing is to add a step. The steps that run a single command need to include ```name```, ```image```, ```command```, and ```args```. Make the name ```echo```, use the image ```alpine:3```, have the command be ```[/bin/echo]``` and the args be ```["Hello World"]```.
   ```yaml
      spec:
        steps:
          - name: echo
            image: alpine:3
            command: [/bin/echo]
            args: ["Hello World!"]
   ```
   * Apply the task to the cluster using the following command: ```kubectl apply -f tasks.yaml```
3. Create a hello-pipeline Pipeline
   ```yaml
   apiVersion: tekton.dev/v1beta1
   kind: Pipeline
   metadata:
   name: hello-pipeline
   spec:
    tasks:
      - name: hello
        taskRef:
        name: hello-world
   ```
   * Apply it to the cluster using the following command: ```kubectl apply -f pipeline.yaml```
   * You are now ready to run your pipeline and see if it works.
4. Run the hello-pipeline
   * Run the pipeline using the Tekton CLI: ```tkn pipeline start --showlog hello-pipeline```
   * You should see the output:
     ```
      PipelineRun started: hello-pipeline-run-9vkbb
      Waiting for logs to be available...
      [hello : echo] Hello World!
     ```


