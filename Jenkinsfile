
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
                bat '''
                    if not exist missing.html exit /b 1
                    echo Test passed
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application'
                bat '''
                    if not exist deploy mkdir deploy
                    copy index.html deploy\\index.html
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}
