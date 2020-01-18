node {
   // Mark the code checkout 'stage'....
   stage 'Checkout' {
      git url: 'https://github.com/rakheeGitHub/game-of-life.git'
   }
   
   // Get the maven tool.
   // ** NOTE: This 'M3' maven tool must be configured
   // **       in the global configuration.           
   def mvnHome = tool 'M3'

   // Mark the code build 'stage'....
   stage 'Build' {
      // Run the maven build
      sh "${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package"
   }
   
   stage 'Archive Test Results' {
      step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/*.xml'])
   }
}
