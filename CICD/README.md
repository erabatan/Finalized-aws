# CICD of your Fortinet resources


## Introduction

As your organization expands, more and more application are developed and moved to the cloud for many reasons: agility, scalability...Your infrastructure grows so rapidly that security of your data and your flows become more and more complex. Because the public cloud providers have a shared responsability model, it is your concern to integrate third party security solutions into your hybrid infrastructure. 
Using templates to test and quickly integrate these solutions make these moves easier. CICD approach helps you test, integrate, modify and adapt your infrastructure changes in a continuous way.


## Design

### About Taskcat
AWS provides a builtin application called <a href="https://aws-quickstart.github.io/auto-testing.html">taskcat</a> which has been designed to test templates (CloudFormation stacks) and generates reports from this activity.
Taskcat application handles the following:
- Powers the Quick Start CI system. Every change that is published to the master branch of a Quick Start runs through TaskCat.
- Stages your code to Amazon S3 for testing in one or more regions.
- Uses a parameters file to pass input parameters to CreateStack.
- Uses runtime injection to dynamically generate stack inputs.
- Collects logs from the CloudFormation stack (including nested stacks).
- Cleans up stacks and staging assets.
- Generates test reports for every requested test region.

TaskCat supports all major Linux distributions and MacOS. (For Windows, use the Bash shell.)

### The added value of this template
Here we use specific AWS services like CodePipeline and CodeBuild to launch a linux container where taskcat will be automatically installed. CodePipeline is able to retrieve your templates from your Github repository before forwarding the content to CodeBuild for technical testing (creates stack, tests and generates reports via taskcat).

After you have installed this template, you will be able to automatically run tests of your templates everytime you commit a change to your github repository. 
Moreover this template generates an API Gateway so as you can launch a test from any API call (Ex: a virtual button on your mobile, a curl command, etc.)

Here are the AWS services involved in this template:
<img class="fit-picture"
     src="/images/workflow.png"
     alt="workflow">

## Deployment

For the deployment, you can use the CloudFormation template.json in AWS CloudFormation console.
Here is the information to provide to the form for a smooth deployment:



## Requirements and limitations

The names of your test scenarii in "ci" folder will be used to name the CloudFormation stacks and generate S3 buckets. Therefore you must use short names without capital letters or any forbidden caracter for S3 service.

## Support
Fortinet-provided scripts in this and other GitHub projects do not fall under the regular Fortinet technical support scope and are not supported by FortiCare Support Services.

## License
[License]: Apache 2.0 (qs-1ops82lkf). Taskcat application is AWS property.
