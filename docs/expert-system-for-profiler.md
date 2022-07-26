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
Logging runtime information in software application is critically useful for understanding the behavior of any app, especially in cases when encountering unexpected scenarios or errors in production environment. Usually, developers have no access to the production and can't use debugger and profilers. Here log data can help.   
Java takes a customizable and extensible approach to logging. Java provides a basic logging API through the java.util.logging package, and it can be implemented in a third party package. When an application makes a logging call, the Logger records the event in a LogRecord and forwards it to the appropriate Handler. The Handler then formats the record using a Layout before sending it a destination such as the console, a file, or another application. Additionally, you can use one or more Filters to specify which Handler should be used for which events. Filters aren’t required, but they give you greater control over the flow of your log messages.

<table width="256px">
  <tr>
    <td><img src="../images/java-log.png"/></td>
  </tr>
  <tr><td align="center">JVM Logger</td></tr>
</table>  

Improper usage of logging can have a significant impact on overall performance of software applications. Here is the most common performance issues when making use of logging:

- Problem 1: logging in the Hot Path. Logging in a portion of the code that’s critical and executed very often is expensive. Unless it’s indispensable, you want to avoid logging here because it could cause an I/O bottleneck.
- Problem 2: expensive operation inside log. Logging can and does impact performance. One of the ways in which this can happen is when developers perform expensive function calls that could be avoided.
```java
log.info(String.format("message %s", expensiveCall()));
```
- Problem 3: excessive Logging. This can happen in an attempt to capture all potentially relevant data.
```java
logger.info("Starting method execution: " + joinPoint.getSignature().getName() + " in class:"+joinPoint.getSignature().getDeclaringTypeName());
Object result = joinPoint.proceed();
logger.info("Exiting method execution: " + joinPoint.getSignature().getName() + " in class:"+joinPoint.getSignature().getDeclaringTypeName());
```
- Problem 4: logging large messages. Consider an example when developer logs responses with payloads that come from external services. Another well known example when logging error with long stack traces.
- Problem 5: slow write operations. By default, logging is blocking. When the runtime executes the log statement, the log gets written on the disk. The speed of writing onto the disk depends a lot on the underlying hardware which may be slow..

   
### Objectives
Here are just a few recommendation to improve logging performance
- Problem 1: logging in the Hot Path.
    - 1. Avoid logging in the Hot Path.
    - 2. Change log filtering, leaving only ERROR logs in the Hot Path.
- Problem 2: expensive operation inside logs.
  - 1. TBD

### Flow 2: [TBD]()


