# Cloud Profiler - Operational Excellence Plan

## Background
Cloud Profiler continuously gathers CPU usage and memory-allocation information from Cloud Applications. It attributes that information to the source code that generated it, helping you identify the parts of applications that are consuming the most resources, and otherwise illuminating application performance characteristics. Cloud Profiler addresses a lot of challenges in profiling Cloud Applications like Elasticity, Security, Data Volume and by itself has a Cloud Application Structure. Cloud Profiler has a Micro Services structure. These services developed in different programming languages C++, Java, Go, JavaScript, Python. Such an Application is really difficult to maintain. This document contains an [Operation Excellence](https://wa.aws.amazon.com/wellarchitected/2020-07-02T19-33-23/wat.pillar.operationalExcellence.en.html) Plan for the Cloud Profiler.

<table width="256px">
  <tr>
    <td><img src="../images/cloud-profiler-arch.png"/></td>
  </tr>
  <tr><td align="center">Cloud Profiler</td></tr>
</table>  


## Objectives
- Improve development velocity: allow development team to work efficiently and focus on adding new features by keeping a clean and healthy codebase. 
- Automate deployments: allow deploying frequent, small, and reversible changes to reduce the scope of a change. This results in easier troubleshooting and faster remediation.
- Mitigate deployment risk: automatically test changes and validate the results as soon as possible, to confirm new features and minimize the risk and impact of failed deployments.
- Enhance system's observability: enable a system to tell when it’s broken, or what is about to break. Build extensive metrics and logging that will allow problem investigation and mitigation.

## Solution

### CI/CD
CI/CD pipeline builds the incremental code changes made by developers, then package them into software deliverables, deploys to the target environment and run tests. Automated tests verify the software functionality and can block deployment due to tests failure. When designed correctly, CI/CD pipelines enforce early defect discovery, increase productivity, and provide faster release cycles. 

<table width="256px">
  <tr>
    <td><img src="../images/ci_cd.png"/></td>
  </tr>
  <tr><td align="center">CI/CD</td></tr>
</table>  


### Static Code Analysis
Static code analysis uncovers defects and infrastructure issues earlier in the CI/CD pipeline. Our approach will perform automated checks against the overall quality of your code, so your developers have more time to focus on what they do best, developing. Proposed tool is [Qodana](https://www.jetbrains.com/qodana/jvm/) by JetBrains. In addition, since developers use different IDE (eclipse, intellij, vscode) we can enforce code styling by running  



### Unit Testing
The goal of unit testing is to isolate each part of the program and show that the individual parts are correct. A unit test provides a strict, written contract that the piece of code must satisfy. As a result, it affords several benefits.
Proposed Frameworks: [Junit](https://junit.org/junit5/), [Pytest](https://docs.pytest.org/en/7.1.x/), JavaScript(?)Proposed unit test coverage ratio is 90%.

### 



- Protect master:
    - 1. Run unitests and integartion tests before submit(merge to master).

- Stability (continues integration test):
- 1. Integration Test (Jenkins Job)
    - Regression Tests (run test application - dedicated to regression tests)
    
    1. Test Gateway endpoint:
        - Open Session
        - Test Mongo for metadata
        - Test Elastic for data
        - Test Data consistency
        - Close Session
    
    2. Test Recomendation
        - Test the number of recomendations
        - Test recomendation validity   
        - 

    2. Metrics based Tests (advanced) 
 
    - 3. Recomendation is running
    - 4. Test Propress

## Milestones

### Milestone 1