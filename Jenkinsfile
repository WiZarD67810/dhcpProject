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
                sh "echo cnam2021 | sudo -S mv var/lib/jenkins/workspace/Git/dhcpd.conf /data"
                sh "echo cnam2021 | sudo -S cp var/lib/jenkins/workspace/Git/dhcpd.conf /data"
                sh "ls -la /data"
                sh "docker-compose up "


            } 
        }
        stage('Stop') {
            steps {
                echo 'Stop docker'
                sh "docker-compose down"
            }
        }
    }
}

