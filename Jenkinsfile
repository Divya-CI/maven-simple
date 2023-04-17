pipeline {
   agent any

   tools {
      // Install the Maven version configured as "M3" and add it to the path.
      maven "M3"
   }

   stages {
      stage('compile') {
         steps {
            bat "mvn clean compile"
         }
         }
      stage("Test") {
          steps {
            bat "mvn clean test"
            
          }

      }
      
   }
}
