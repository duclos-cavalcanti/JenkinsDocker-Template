# Jenkins-Pipeline-Template

## Initial Steps
1. Pull jenkins docker
```
docker pull jenkins/jenkins
```

2. Makefile targets
```
TODO
```

## Jenkins

### Jobs
* Freestyle
    Useful for simple, single tasks like running tests.

* Pipeline
    Whole delivery cycle, like test + build + deploy

* Multibranch Pipeline
    like pipeline but for multiple branches of one repo

### Credentials
ID:
    Important, their names are referenced by Jenkinsfiles.
Scopes:
* System
    Only available on Jenkins server, not for Jenkins jobs.

* Global
    Everywhere accessible

* Project
    Only usable in multibranch pipelins, limited to the project in question

### Branch Discoery
Example Regex
```
.*dev|.*feature
```

### Pipeline Syntax
* Scripted
    First syntax, uses groovy engine, nodes are scripted through groovy script. It has
    advanced capabilities, vaery flexible.

* Declarative
    Predefined structure, easier to get started, more rigig.
