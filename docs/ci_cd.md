# Cloud Profiler CI / CD

## Background

## Flow

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
