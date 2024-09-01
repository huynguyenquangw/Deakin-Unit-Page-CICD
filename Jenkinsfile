pipeline {
    agent any

    environment {
        DIRECTORY_PATH = './'
        TESTING_ENVIRONMENT = 'Staging'
        PRODUCTION_ENVIRONMENT = 'JAKE'
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetching the source code from the directory path: ${env.DIRECTORY_PATH}..."
                sleep 1
                echo "Compiling the code and generating necessary artifacts..."
                sleep 2
                echo 'Building the project...'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Running code analysis...'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
            }
        }
    }
}