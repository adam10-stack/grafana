pipeline {
    agent any

    stages {
    
        stage('Run install grafana') {
            steps {
                sh '''
                    sudo dnf install grafana -y
                '''
            }
        }

        stage('start service grafana') {
            steps {
                sh '''
                    sudo systemctl enable --now grafana-server
                    sudo systemctl status grafana-server
                '''
            }
        }
        
        stage('set-up firewall') {
            steps {
                sh '''
                    sudo firewall-cmd --add-port=3000/tcp --permanent
                    sudo firewall-cmd --reload
                '''
            }
        }
        
        stage('grafana Test Connection') {
            steps {
                sh 'curl -vk http://grafana:3000'
            }
        }
    }
}
