pipeline {
    agent none
    environment {
      registry = "ggkioka/adneom"
      registryCredential = 'dockerhub'
    }
    stages {
        stage('Build') {
          agent {
            docker {
              alwaysPull true
              args '-e HOME=/tmp'
              image 'openjdk:11-stretch'
            }
          }
            steps {
                sh './gradlew build'
				        stash(name: 'build-artifact')
            }
        }
        stage('Build Docker') {
            steps {
                //docker.build(registry + "/new_image:latest")
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
