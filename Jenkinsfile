pipeline {
    agent any
    
    environment {
        // Define SSH credentials for connecting to the target EC2 instance
        SSH_CREDENTIALS = 'sshcred'
        REMOTE_HOST = '172.31.88.55' //private ip of apache web-server
        REMOTE_USER = 'ubuntu'
        REMOTE_DIR = '/var/www/html/' // Destination directory on the target EC2 instance
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                git 'https://github.com/SreelekhaB77/Transport-Management-System.git'
            }
        }
        stage('Deploy') {
            steps {
                // Copy project files to the target EC2 instance
                script {
                    sshagent(['sshcred']) {
                        sh "scp -o StrictHostKeyChecking=no -r ./* ${REMOTE_USER}@${REMOTE_HOST}:${REMOTE_DIR}"
                    }
                }
            }

    }
    
    
}
}
