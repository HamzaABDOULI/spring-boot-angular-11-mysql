pipeline {
    agent any

    options {
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



      }


}