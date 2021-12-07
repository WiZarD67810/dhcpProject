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
                sh "docker-compose up"
                sh "pwd"
                sh "ls /"
                sh "cat dhcpd.conf"
                sh "echo cnam2021 | sudo -S cp dhcpd.conf /data"
                sh "ls /data"
                sh "service --status-all"
                sh "service isc-dhcp-server restart"               
                sh "service isc-dhcp-server status"


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

