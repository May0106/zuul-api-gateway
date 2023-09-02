pipeline {
    agent { docker { image 'maven:3.9.4-eclipse-temurin-17-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }

        stage("test"){
            steps{
                echo "-----------unit test started-----------"
                sh 'mvn surefire-report:report'
                echo "-----------unit test ended-------------"
            }
        }

        stage('SonarQube analysis') {
        environment {
          scannerHome = tool 'sonar-scanner'
            }    
            steps{
            withSonarQubeEnv('sonarqube-server') {
              sh "${scannerHome}/bin/sonar-scanner"   

    }
     
  }    
}
    }
}







