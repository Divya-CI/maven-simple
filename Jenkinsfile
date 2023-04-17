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
      stage("Deploy") {
        steps {
           bat "mvn clean install"
           
        }
        }
   }
      post {
         always {
            echo"Archiving the code..."
            archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            archiveArtifacts artifacts: 'target/surefire-reports/*.txt'
         
      }
     }
}
      
  

