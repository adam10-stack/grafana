pipeline {
    agent any

    stages {
    
        stage('Install Grafana') {
            steps {
                sh '''
                    sudo dnf install grafana -y
                '''
            }
        }
       
        stage('Set-up Firewall for Grafana') {
            steps {
                sh '''
                    sudo firewall-cmd --add-port=3000/tcp --permanent
                    sudo firewall-cmd --reload
                '''
            }
        }
		
		stage('Start Grafana Service') {
            steps {
                sh '''
                    sudo systemctl enable --now grafana-server
                    sudo systemctl status grafana-server
                '''
            }
        }
        
        stage('Test Grafana Connection') {
            steps {
                sh 'get http://grafana:3000'
            }
        }
    }
}
