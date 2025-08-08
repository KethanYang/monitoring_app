pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/KethanYang/monitoring_app.git'
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Build step - verifying repo"'
                sh 'ls -la'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "No tests for now"'
            }
        }
        stage('Deploy') {
            steps {
                sshagent(['monitoring-ssh']) {
                    sh '''
                    scp -r ./* ethan2@192.168.56.31:/home/ethan2/monitoring_app/
                    ssh ethan2@192.168.56.31 'sudo systemctl restart monitoring.service'
                    '''
                }
            }
        }
    }
}
