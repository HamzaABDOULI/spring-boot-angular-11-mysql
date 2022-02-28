pipeline {
    agent any

    stages {
        stage('Build SpringBoot Project') {
            steps {
                echo 'Start Building the SpringBoot project'
                dir('spring-boot-server'){
                    sh 'mvn install clean' 
             }
            }
        }         

        stage('BuildAngular Project') {
            steps {
                echo 'Start Building the Angular project'
                dir('angular-11-client'){
                    bat 'npm install'
                    bat 'npm run ng -- build'
                    bat 'tar.exe cf dist.zip dist' 
                }
            }
        }

      }

      post {
        always {
            archiveArtifacts artifacts: '**/*.jar, **/angular-11-client/dist.zip', onlyIfSuccessful: true
        }
    }
}