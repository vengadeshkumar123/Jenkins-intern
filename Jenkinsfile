
pipeline {
    agent any

    environment {
        DEPLOY_DIR = "/var/www/html"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'Yhttps://github.com/vengadeshkumar123/Jenkins-intern'
            }
        }

        stage('Build') {
            steps {
                sh '''
                    test -f index.html
                    test -d assets
                    test -d images

                    echo "Website files verified"
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    sudo cp -r assets images index.html ${DEPLOY_DIR}/

                    sudo systemctl reload nginx
                '''

                echo "Website deployed successfully"
            }
        }
    }

    post {
        success {
            echo "Deployment Successful!"
        }

        failure {
            echo "Deployment Failed!"
        }
    }
}
