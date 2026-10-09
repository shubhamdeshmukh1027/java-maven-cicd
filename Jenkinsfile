```groovy
pipeline {
    agent any

    stages {
        stage('Check Java and Maven') {
            steps {
                echo 'Checking Java version...'
                sh 'java -version'

                echo 'Checking Maven version...'
                sh 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Java Maven project...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging Java application...'
                sh 'mvn package'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'FAILURE: Pipeline failed. Check Console Output for details.'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
```
