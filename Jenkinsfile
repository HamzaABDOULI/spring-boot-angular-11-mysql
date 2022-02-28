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

        stage('BuildAngular Project') {
            steps {
                echo 'Start Building the Angular project'
                dir('angular-11-client'){
                    bat 'npm install'
                    bat 'npm run ng -- build' 
                }
            }
        }

        stage('Archive') {
            steps {
                echo 'Archive dist folder'
                dir('angular-11-client'){
                    bat 'tar.exe cf dist.zip dist'
                    archive 'dist.zip'
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