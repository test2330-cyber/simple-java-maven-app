pipeline {
    agent any
    tools {
        jdk 'JDK21'
        maven 'Maven'
    }
    environment {
        JAVA_HOME = '/usr/lib/jvm/java-21-openjdk-amd64'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the Git repository...'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'java -version'
                sh 'mvn -version'
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }
    }
    post {
        success {
            echo '✅ Build and tests passed!'
        }
        failure {
            echo '❌ Build failed. Check the console output for details.'
        }
    }
}
