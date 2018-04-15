pipeline {
  agent { label 'linux'}
  node {
    jdk = tool name: 'Java 8'
    env.JAVA_HOME = "${jdk}"

    echo "jdk installation path is: ${jdk}"

    // next 2 are equivalents
    sh "${jdk}/bin/java -version"

    // note that simple quote strings are not evaluated by Groovy
    // substitution is done by shell script using environment
    sh '$JAVA_HOME/bin/java -version'
  }
  tools {
    maven 'maven-3.5.3'
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
        junit '**/target/surefile-reports/TEST-*.xml'
      }
    }
    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }
  }
}
