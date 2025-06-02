pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/adam10-stack/grafana.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t grafana-custom:latest .'
            }
        }

        stage('Run Grafana Container') {
            steps {
                sh '''
                    docker stop grafana || true
                    docker rm grafana || true
                    docker run -d -p 3000:3000 --name grafana grafana-custom:latest
                '''
            }
        }

        stage('Katalon Test (Manual Trigger)') {
            steps {
                input "Run Katalon test?"
                sh 'echo "Run Katalon test here"'
            }
        }
    }
}
