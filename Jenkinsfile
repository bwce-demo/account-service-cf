pipeline {
  agent any
  stages {
    stage('Initialize') {
      steps {
        tool(name: 'Maven-3.3.9', type: 'Maven')
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