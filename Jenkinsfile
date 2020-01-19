pipeline {
   agent any {
      stages {
         stage ('Build') {
            //Get the maven tool.
            def mvnHome = tool 'M3'
            
            //build
            sh "${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package"             
         }
         
         stage ('Archive Test Results') {
            step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/*.xml'])
         }
      }
   }
}
     
