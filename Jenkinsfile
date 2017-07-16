pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/bwce-demo/account-service-cf.git'
      }
    }
    stage('Test') {
      steps {
        sh 'cd *.module'
        sh 'mvn clean sonar:sonar'
      }
    }
  }
}