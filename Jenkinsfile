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
                sh "docker-compose up -d"
                sh "ls"
                sh "pwd"
                sh "cd /home/.."
                sh "pwd"
                sh "ls"
                sh "echo 'cnam2021' | sudo -S cp /var/lib/jenkins/workspace/Git/dhcpd.conf /data/dhcpd.conf "
                sh "cat /data/dhcpd.conf"

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

