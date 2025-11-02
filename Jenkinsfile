pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository from GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Build stage - listing files...'
                sh 'ls -l'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying sample.html to Apache web server...'
                sh '''
                sudo cp sample.html /var/www/html/
                sudo systemctl restart apache2
                '''
            }
        }
    }

    post {
        success {
            echo '🎉 Deployment Successful!'
        }
        failure {
            echo '❌ Deployment Failed.'
        }
    }
}
