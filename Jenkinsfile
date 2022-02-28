pipeline {
    agent any
    stages {
        stage('Build') { 
           steps{
               echo'buildinggggggggggggggggg'
               dir('spring-boot-server'){
                sh 'mvn clean install'
            } 
           }
        }
    }
}