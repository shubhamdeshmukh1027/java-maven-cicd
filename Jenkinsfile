
pipeline {
    agent any

    stages {
        stage('Check Java and Maven') {
            steps {
                echo 'Checking Java version...'
                sh 'java -version'

                echo 'Checking Java compiler...'
                sh 'which java'
                sh 'which javac'
                sh 'javac -version'

                echo 'Checking JAVA_HOME...'
                sh 'echo $JAVA_HOME'
                sh 'readlink -f $(which javac)'

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
            echo 'SUCCESS: Build, Test, and Package completed!'
        }

        failure {
            echo 'FAILURE: Check the Console Output for details.'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
