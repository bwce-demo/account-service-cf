pipeline {
  agent any
  stages {
    stage('Initialize') {
      steps {
        tool(name: 'Maven', type: 'Maven-3.3.9')
      }
    }
    stage('Checkout') {
      steps {
        git 'https://github.com/bwce-demo/account-service-cf.git'
      }
    }
    stage('Test') {
      steps {
        sh '''cd *.module
&& mvn clean sonar:sonar'''
      }
    }
  }
}