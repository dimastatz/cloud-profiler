# Expert Engine for Java Logging Frameworks

## Background
Logging runtime information in software applications is useful for understanding the behavior of any app. Log files can save a lot of time by providing clues into the cause of the problem, and into the state of the system at the time it happened. Also, logging can be useful for auditing purposes, gathering statistics, extracting business intelligence and a variety of other tasks. 
However, logging can be a source of performance problems. The document provides a software design for the expert system that helps developers to understand the root cause of performance problems that can occur in [Java Logging Frameworks](https://en.wikipedia.org/wiki/Java_logging_framework). 

## Requirements

### Functional
- Actor 1: Cloud Profiler
    - Start JVM Profiling Session
    - Write Profiling Data to DB
    - Stop JVM Profiling Session

- Actor 2: Profiling Expert
    - Run any [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) operation on Knowledge DB

- Actor 3: Reasoning Engine
    - Read Profiling Data from Profiling Sessions DB
    - Read knowledge from Knowledge DB
    - Perform Reasoning
    - Write Reasoning Flow and Result to Reasoning DB

- Actor 4: User
    - View reasoning flow and result
    - ?

### Non-Functional
1. Handle Scale of 1000 profiling sessions. Each session generates up to 100Kb/sec
2. Knowledge D  
