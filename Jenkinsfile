pipeline {
    agent any

    environment {
        APP_NAME = "my-node-website"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/mimashinde25/my-node-website.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Deploy with PM2') {
            steps {
                sh '''
                pm2 stop $APP_NAME || true
                pm2 start app.js --name $APP_NAME
                pm2 save
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful'
        }
        failure {
            echo '❌ Deployment failed'
        }
    }
}

