pipeline {
    agent any
    stages {
        stage('Build') { 
           dir('spring-boot-server'){
            sh 'mvn clean install'
            } 
        }
    }
}