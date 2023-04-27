pipeline {
   agent any
   triggers {
  pollSCM '* * * * *'
}

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
      
      stage("email notification"){
         steps {
            emailext (attachLog: true, body: 'This is a sample mail', subject: 'This is extended email test', to: 'testjenkins49@gmail.com')
         }
      
   }
   }
      post {
         always {
            echo"Archiving the code..."
            archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            archiveArtifacts artifacts: 'target/surefire-reports/*.txt'
            publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target/surefire-reports/', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
      }
     }
}

 


