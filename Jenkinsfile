pipeline {
  agent { label 'linux'}
  tools {
    maven 'maven-3.5.3'
    jdk 'Java 8'
  }
  stages {
    stage('checkout') {
      steps {
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
        junit "target/surefile-reports/TEST-*.xml"
            //    target/surefire-reports
      }
    }
    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }
  }
}
