pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh './gradlew build'
				stash(name: 'build-artifact')
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}