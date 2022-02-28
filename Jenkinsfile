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
        stage('Download') {
            steps {
                bat 'echo "artifact file" > generatedFile.txt'
             }
            }
        }

        stage('BuildAngular Project') {
            steps {
                echo 'Start Building the Angular project'
                dir('angular-11-client'){
                    bat 'npm install'
                    bat 'npm run ng -- build' 
             }
            }
        }
      }

      post {
        always {
            archiveArtifacts artifacts: 'generatedFile.txt', onlyIfSuccessful: true
        }
    }
}