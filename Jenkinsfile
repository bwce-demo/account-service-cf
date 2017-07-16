node {
   def mvnHome
   stage('Checkout') {
      git 'https://github.com/rishikeshpalve/bwce-account-service.git'
      mvnHome = tool 'Maven-3.3.9'
   }
   stage('Test') {
      // Run the maven build
      if (isUnix()) {
         sh "cd ./AccountService.module && '${mvnHome}/bin/mvn' clean sonar:sonar -X"
      } else {
         bat(/cd .\AccountService.module && "${mvnHome}\bin\mvn" -f .\AccountService.module\pom.xml clean sonar:sonar -X/)
      }
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
          sh "cd .."
         sh "'${mvnHome}/bin/mvn' -f ./AccountService.parent/pom.xml -Dmaven.test.failure.ignore clean initialize package"
      } else {
         bat(/"${mvnHome}\bin\mvn" .\AccountService.parent\pom.xml -Dmaven.test.failure.ignore clean initialize package/)
      }
   }
   stage('Deploy') {
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -f ./AccountService.parent/pom.xml -Dmaven.test.failure.ignore initialize cf:push"
      } else {
         bat(/"${mvnHome}\bin\mvn" -f .\AccountService.parent\pom.xml -Dmaven.test.failure.ignore initialize cf:push/)
      }
   }
}
