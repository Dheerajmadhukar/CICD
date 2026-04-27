pipeline {
    agent any

    stages {
        stage('Update the repo') {
            steps {
                sh '''
                cd /var/lib/jenkins/workspace/demo1
                git pull --rebase origin main
                '''
            }
        }
        stage('Stop & Remove Previous Container & image') {
            steps {
                sh '''
                sudo docker stop demo_webserver || true
                sudo docker rm -f demo_webserver || true
                sudo docker rmi -f demo1:latest || true
                '''
            }
        } 
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
                    sudo docker run -d -p 80:80 --name demo_webserver demo1:latest
                '''
            }
        }
    }
}
