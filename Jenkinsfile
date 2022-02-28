pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Hello Hammmza'
                dir("spring-boot-server"){
                    sh 'mvn clean install'
             }
            }
        }
    }
}