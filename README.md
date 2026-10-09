# Java Maven CI/CD Pipeline Using Jenkins

## Project Overview

This project demonstrates a Continuous Integration and Continuous Delivery (CI/CD) pipeline for a Java application using Maven, Jenkins, Git, and GitHub.

## Technologies Used

* Java 21
* Apache Maven
* Jenkins
* Git and GitHub
* JUnit 5
* Linux (Ubuntu)

## Project Features

* Automated source code checkout from GitHub
* Java application compilation
* Automated unit testing
* Maven packaging into a JAR file
* Jenkins pipeline execution and build status reporting

## Pipeline Stages

1. Check Java and Maven
2. Build
3. Test
4. Package

## Project Structure

```text
java-maven-cicd/
├── src/
│   ├── main/java/com/example/App.java
│   └── test/java/com/example/AppTest.java
├── pom.xml
└── Jenkinsfile
```

## Build Output

The Maven package stage generates a JAR file inside the `target/` directory.

## How It Works

1. Source code is stored in GitHub.
2. Jenkins fetches the repository.
3. Maven compiles the Java application.
4. JUnit executes unit tests.
5. Maven packages the application into a JAR file.

## Project Outcome

Successfully configured and executed a Jenkins CI/CD pipeline that builds, tests, and packages a Java Maven application.

## Author

Shubham Deshmukh
