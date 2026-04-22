pipeline {
    agent any

    stages {
        stage('Build the docker image') {
            steps {
                sh '''
                    sudo docker build . -t demo1:latest
                '''
            }
        }
        stage('Deploy a container') {
            steps {
                sh '''
                    sudo docker run -d -p 80:80 --name demo_webserver httpd:latest
                '''
            }
        }
    }
}
