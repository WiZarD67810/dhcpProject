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
                sh "hostname"
                sh "echo 'cnam2021' | sudo -S cp dhcpd.conf /etc/dhcp/ "
                sh "ls /etc/dhcp/"
                sh "cat /etc/dhcp/dhcpd.conf"
                sh "ls -la /etc/dhcp/dhcpd.conf"
                sh "echo 'cnam2021' | sudo -S service isc-dhcp-server restart"
                sh "echo 'cnam2021' | sudo -S service isc-dhcp-server status"

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

