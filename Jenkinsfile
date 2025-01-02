pipeline {
  agent any
  environment {
    PATH="/opt/maven/bin:$PATH"
  }
    stages {
      stage ("build") {
        steps {
          sh " mvn clean deploy "
        }
      }
      stage ("SonarQube Analysis") {
        environment {
          scannerHome = tool 'saidemy-sonar-scanner'
        }
        steps {
          with SonarQubeEnv('saidemy-sonarqube-server') {
            sh "${scannerHome}/bin/sonar-scanner"
            }
         }
       }
     }
  }
