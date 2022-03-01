pipeline {
    agent any

    options {
        buildDiscarder(
            logRotator(
            // number of build logs to keep
            numToKeepStr:'5',
            // history to keep in days
            daysToKeepStr: '15',
            // artifacts are kept for days
            artifactDaysToKeepStr: '15',
            // number of builds have their artifacts kept
            artifactNumToKeepStr: '5'
            )
        )
    }

    tools {
        maven "maven3.8.4"
        jdk "jdk1.8"
    }
    stages {

        stage('Initialize'){
            steps{
                echo '========^^^^^^ Initialize ^^^^^^========'
                echo "PATH = ${M2_HOME}/bin:${PATH}"
            }
        }
        stage('Build SpringBoot Project') {
            steps {
                echo '========^^^^^^ Start Building the SpringBoot project ^^^^^^========'
                dir('spring-boot-server'){
                    bat 'mvn install clean' 
             }
            }
        }         

        stage('BuildAngular Project') {
            steps {
                echo '========^^^^^^ Start Building the Angular project ^^^^^^========'
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