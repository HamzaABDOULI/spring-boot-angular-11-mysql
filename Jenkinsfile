import jenkins.model.Jenkins
import hudson.model.Job

MAX_BUILDS = 20

for (job in Jenkins.instance.items) {
  println job.name

  def recent = job.builds.limit(MAX_BUILDS)

  for (build in job.builds) {
    if (!recent.contains(build)) {
      println "Preparing to delete: " + build
      build.delete()
    }
  }
}


pipeline {
    agent any

    tools {
        maven "maven3.8.4"
        jdk "jdk1.8"
    }

    stages {

        stage('Initialize'){
            steps{
                echo 'Initialize'
                echo "PATH = ${M2_HOME}/bin:${PATH}"
            }
        }
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