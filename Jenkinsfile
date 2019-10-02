pipeline {
    agent none
    environment {
      registry = "ggkioka/adneom"
      registryCredential = 'dockerhub'
    }
    stages {
        stage('Build') {
          agent {
            label 'openjdk-11'
          }
            steps {
                sh './gradlew build'
				        stash(name: 'build-artifact')
            }
        }
        stage('Build Docker') {
            steps {
              echo 'Deploying....'
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
