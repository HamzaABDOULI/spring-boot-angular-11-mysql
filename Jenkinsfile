pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Hello Hammmza'
                dir('spring-boot-angular-11-mysql/spring-boot-server/'){
                    sh 'mvn clean install'
             }
            }
        }
    }
}