pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Start Buiiiilding'
                dir('spring-boot-server'){
                    bat 'mvn install clean'
                
             }
            }
        }
    }
}