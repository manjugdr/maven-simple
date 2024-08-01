pipeline {
   agent any

   // tools {
      // Install the Maven version configured as "M3" and add it to the path.
      // maven "M3"
     tools {
        maven 'M3' // Ensure 'M3' matches the name configured in Jenkins
    // }
   }

   stages {
      stage('Build') {
         steps {
            // Get some code from a GitHub repository 
            git 'https://github.com/jglick/simple-maven-project-with-tests.git'
            sh "mvn -Dmaven.test.failure.ignore=true clean compile"
         }
         }
      stage("Test") {
          steps {
            git 'https://github.com/jglick/simple-maven-project-with-tests.git'  
            sh "mvn -Dmaven.test.failure.ignore=true clean test"
            
          }

      }
      stage("Deploy") {
          steps {
            git 'https://github.com/jglick/simple-maven-project-with-tests.git'  
            sh "mvn -Dmaven.test.failure.ignore=true clean install"
            
          }
          post {
              success {
                  archiveArtifacts 'target/*.jar'
              }

          }


      }

      }
   }

