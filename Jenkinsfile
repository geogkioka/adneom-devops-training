pipeline {
    agent none
    environment {
      registry = "ggkioka"
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
            agent {
              label 'docker'
            }
            steps {
              unstash 'build-artifact'
              dir(path: 'asgard-rest') {
                script {
                    docker.build(registry + "/asgard-rest:latest")
                }
            }

            dir(path: 'asgard-web') {
              script {
                  docker.build(registry + "/asgard-web:latest")
                  }
            }
          }
        }
        stage('Deploy') {
           agent {
           label 'docker-slave'
         }
         steps {
           script {
             sh "/snap/bin/docker-compose up -d"
             echo 'Open you browser to http://localhost:5580/'
           }
         }
        }
    }
}
