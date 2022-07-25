# An Expert System for Software Profiling

## Background
Profiling is a dynamic code analysis. Profilers capture characteristics of the application as it runs, and then developers use this information to make applications faster and more efficient. For example, one of the most known JVM profilers is [JProfiler](https://www.ej-technologies.com/resources/jprofiler/help/doc/JProfiler.pdf). JProfiler collects the following data: methods calls data (aka CPU profiling), allocations (heap allocations, GC), threads and locks and data from higher level subsystems like JDBC, HTTP, etc. All collected data is shown in JProfiler's UI. By examining data on Jprofiler UI, developers can figure out if there any problem in the profiled application and hopefully find a root cause for it. However, it is really hard to make sense of profilers output. One should be an expert with many years of a hands-on experience in Java programming language in order to make sense of data that is shown on JProfiler UI.  
This document describes the design of the Knowledge-Based (Expert) System for Software Profiling. Knowledge-Based systems are computer programs that use [AI](https://en.wikipedia.org/wiki/Artificial_intelligence) technologies to simulate the judgment and behavior of a human or an organization that has expertise and experience in a particular field. Expert systems are usually intended to complement, not replace humans.

<table width="256px">
  <tr>
    <td><img src="../images/expert-systems.png"/></td>
  </tr>
  <tr><td align="center">Expert Systems</td></tr>
</table>  


## Requirements

### Functional Requirements
- Actor 1: Domain Expert
    - Knowledge Acquisition: gather the knowledge about profiling 
    - Knowledge Engineering: build the knowledge database 

- Actor 2: Non-Expert User
    - Query Inference Engine
- Actor 3: Cloud Profiler
    - Generate profiling sessions aka working DB

### Non-Functional Requirements
[TBD]()

## High-Level Design
The Profiling Expert System consisting of the Knowledge and Inference Engine.
- Knowledge is a dataset that contains facts about the profiling domain
- Inference Engine is a program that processes the knowledge and solve the problem described in the working DB  


## Low-Level Design

### Flow 1: Profiling JVM Logging Frameworks

### Problem Statement
Logging runtime information in software application is critically useful for understanding the behavior of any app, especially in cases when encountering unexpected scenarios or errors in production environment. Usually, developers have no access to the production and can't use debugger and profilers. Here log data can help. However, improper usage of logging can have a significant impact on overall performance of software applications. 

<table width="256px">
  <tr>
    <td><img src="../images/java-log.png"/></td>
  </tr>
  <tr><td align="center">JVM Logger</td></tr>
</table>  

Here is the most common performance issues when making use of logging:

- Logging in the Hot Path: logging in a portion of the code that’s critical and executed very often is expensive. Unless it’s indispensable, you want to avoid logging here because it could cause an I/O bottleneck.
- Expensive operation inside log: logging can and does impact performance. One of the ways in which this can happen is when you perform expensive function calls that could be avoided. Consider the following line:
```java
log.info(String.format("message %s", expensiveCall()));
```
- Incorrect log level (DEBUG, INFO)
- Writing big messages
- Bufferless IO
- Using a single file for all logs 
   


### Objectives


### Flow 2: [TBD]()


