pipeline {
    agent { label 'linux' }
    tools {
        maven 'maven-3.5.3'
    }
    stages{
        stage('Checkout'){
            steps {
                echo 'Checking out code'
                echo ' https://github.com/mcclayac/myProject.git'
                git 'https://github.com/mcclayac/myProject.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }   junit 'target/surefire-reports/TEST-*.xml'
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }
}