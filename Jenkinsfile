pipeline {
    agent any
    stages {
        stage('Build SpringBoot Project') {
            steps {
                echo 'Start Building the SpringBoot project'
                dir('spring-boot-server'){
                    bat 'mvn install clean' 
             }
            }
        }         
      }

      post {
        always {
            archiveArtifacts artifacts: '**/*.jar', onlyIfSuccessful: true
        }
    }
}