pipeline {
    agent any
    stages {
        stage('Install stuff') {
            steps {
                echo 'Installation docker'
                sh "docker-compose -v"
                sh "docker -v"
                //sh "docker-compose down"
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
                sh "ls"
                sh "echo cnam2021 | sudo -S cp dhcpd.conf /data"
                sh "cd data"
                sh "cat dhcpd.conf"
                sh "service --status-all"
                sh "cat /etc/default/isc-dhcp-server"
                sh "echo cnam2021 | sudo -S echo DHCPDv4_CONF=/var/lib/jenkins/workspace/Git/data/dhcpd.conf >> /etc/default/isc-dhcp-server"
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

