
pipeline {
    agent any

    tools {
        maven 'Maven-3.9'
        jdk 'JDK-17'
    }

    stages {
        stage('1. Checkout Code') {
            steps {
                echo 'Fetching source code from GitHub...'
                checkout scm
            }
        }

        stage('Check Java and Maven') {
            steps {
                echo 'Checking Java version...'
                sh 'java -version'

                echo 'Checking Java compiler...'
                sh 'javac -version'

                echo 'Checking Maven version...'
                sh 'mvn -version'
            }
        }

        stage('2. Build') {
            steps {
                echo 'Compiling the Java application...'
                sh 'mvn clean compile'
            }
        }

        stage('3. Unit Test') {
            steps {
                echo 'Running unit tests...'
                sh 'mvn test'
            }
            post {
                always {
                    junit allowEmptyResults: true,
                          testResults: '**/target/surefire-reports/*.xml'
                }
            }
        }

        stage('4. Package') {
            steps {
                echo 'Packaging application into JAR/WAR...'
                sh 'mvn package -DskipTests'
            }
        }

        stage('5. Deploy') {
            steps {
                echo 'Deploying application artifact...'
                sh '''
                    set -eu

                    JAR_FILE=$(find target -maxdepth 1 -type f -name '*.jar' ! -name '*-sources.jar' ! -name '*-javadoc.jar' | head -n 1)

                    if [ -z "$JAR_FILE" ]; then
                        echo "ERROR: No JAR file found in target directory."
                        exit 1
                    fi

                    mkdir -p /tmp
                    cp "$JAR_FILE" /tmp/deployed-app.jar

                    echo "Deployment artifact copied successfully."
                    ls -lh /tmp/deployed-app.jar
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }
    }
}
