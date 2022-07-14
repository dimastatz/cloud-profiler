# Cloud Profiler - Regression Testing 

## Background
Cloud Profiler continuously gathers CPU usage and memory-allocation information from Cloud Applications. It attributes that information to the source code that generated it, helping you identify the parts of applications that are consuming the most resources, and otherwise illuminating applications performance characteristics. Cloud Profiler addresses a lot of challenges in profiling Cloud Applications like Elasticity, Security, Data Volume and by itself has a Cloud Application Structure. Cloud Profiler has a Micro Services structure. These services developped in diffrent programming languages C++, Java, Go, JavaScript, Python. Such an Application is really difficult to maintain. This document contains a bunch of ideas about implementing code quality validations, regressions and e2e testing of CloudProfiler

## Objectives

### Functional

### Non-Functional

- Code Quality:
    - 1. Code Coverage (Informative)
    - 2. Static Analysis (Informative)

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
