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
                sh "echo 'cnam2021' | sudo -S su"
                sh "pwd"
                sh "hostname"
                sh "sudo cp dhcpd.conf /etc/dhcp/ "
                sh "ls /etc/dhcp/"
                sh "cat /etc/dhcp/dhcpd.conf"
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
z