node {
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/kumaraswamym/shoppingcart'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      
   }
   stage('Build') {
      // Run the maven build
      
         if (isUnix()) {
            sh '"$MAVEN_HOME/bin/mvn" -Dmaven.test.failure.ignore clean package'
         } else {
            bat(/"%MAVEN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean package/)
         }
      
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.war'
   }
}
