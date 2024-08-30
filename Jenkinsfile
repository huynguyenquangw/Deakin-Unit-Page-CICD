pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    // Use Maven to build the project
                    echo 'Building the project...'
                    sh 'mvn clean install'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit and integration tests...'
                    sh 'mvn test'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo 'Running code analysis...'
                    // Assuming SonarQube is set up
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo 'Performing security scan...'
                    // Example command for OWASP ZAP
                    sh 'zap-cli start && zap-cli quick-scan http://localhost'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to staging...'
                    // Commands to deploy to staging
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on staging...'
                    // Integration testing commands
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to production...'
                    // Commands to deploy to production
                }
            }
        }
    }
    // post {
    //     always {
    //         mail to: 'your-email@example.com',
    //              subject: "Pipeline Status: ${currentBuild.fullDisplayName}",
    //              body: "The status of the pipeline is: ${currentBuild.currentResult}\n\nCheck Jenkins for details.",
    //              attachLog: true
    //     }
    // }
}