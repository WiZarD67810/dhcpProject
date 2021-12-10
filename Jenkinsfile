pipeline {
    agent any
    stages {
        stage('Install stuff') {
            steps {
                echo 'Installation docker'
                sh "docker-compose -v"
                sh "docker -v"
                sh "docker-compose down"
		        sh "docker network prune -f"
                sh "docker-compose build"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploiement docker'
                sh "ls -la"
                sh "pwd"
                sh "ls -la data"
                sh "docker-compose up"
                sh "ifconfig"


            } 
        }
        stage('Stop') {
            steps {
                echo 'Stop docker'
            }
        }
    }
}

