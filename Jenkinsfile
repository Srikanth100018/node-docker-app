pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/Srikanth100018/node-docker-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t node-docker-app:0.0.1 .
                docker tag node-docker-app:0.0.1 b211359/node-docker-app:0.0.1
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push b211359/node-docker-app:0.0.1'
            }
        }
        
        stage('Create container') {
            steps {
                sh 'docker run -d -p 3000:8080 b211359/node-docker-app:0.0.1'
            }
        }



    }
}
