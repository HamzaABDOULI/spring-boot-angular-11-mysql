pipeline {
    agent any

    options {
        echo '========^^^^^^ Delete Old Builds ^^^^^^========'
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
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
            echo '========^^^^^^ Archive Artifacts ^^^^^^========'
            archiveArtifacts artifacts: '**/*.jar, **/angular-11-client/dist.zip', onlyIfSuccessful: true
        }
    }
}