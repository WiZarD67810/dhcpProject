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
                sh "docker-compose up -it --rm --init --net host -v '$(pwd)/data':/data networkboot/dhcpd eth0"
                sh "ls"
                sh "pwd"
                sh "mkdir data"
                sh "cd data"
                sh "pwd"
                sh "ls"
                sh "echo 'cnam2021' | sudo -S cp ../dhcpd.conf /data"
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

