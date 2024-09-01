pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "./"
        TESTING_ENVIRONMENT = "Staging"
        PRODUCTION_ENVIRONMENT = "JAKE"
    }

    stages {
        stage("Build") {
            steps {
                script {
                    echo "Building the code using Maven..."
                    echo "Tool: Maven"
                }
            }
        }

        stage("Unit and Integration Tests") {
            steps {
                script {
                    echo "Running unit tests and integration tests..."
                    echo "Tools: JUnit for unit testing, Selenium for integration testing"
                }
            }
            post {
                success {
                    script {
                        emailext(
                            to: "s2241473112@deakin.edu.au",
                            subject: "Unit and Integration Tests Succeeded: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                            body: "The Unit and Integration Tests stage of ${env.JOB_NAME} build ${env.BUILD_NUMBER} completed successfully.",
                            attachLog: true
                        )
                    }
                }
                failure {
                    script {
                        emailext(
                            to: "s2241473112@deakin.edu.au",
                            subject: "Unit and Integration Tests Failed: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                            body: "The Unit and Integration Tests stage of ${env.JOB_NAME} build ${env.BUILD_NUMBER} failed. Please check the attached logs.",
                            attachLog: true
                        )
                    }
                }
            }
        }

        stage("Code Analysis") {
            steps {
                script {
                    echo "Performing code analysis using SonarQube..."
                    echo "Tool: SonarQube"
                }
            }
        }

        stage("Security Scan") {
            steps {
                script {
                    echo "Performing security scan to identify vulnerabilities..."
                    echo "Tool: OWASP Dependency Check"
                }
            }
            post {
                success {
                    script {
                        emailext(
                            to: "s2241473112@deakin.edu.au",
                            subject: "Security Scan Succeeded: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                            body: "The Security Scan stage of ${env.JOB_NAME} build ${env.BUILD_NUMBER} completed successfully.",
                            attachLog: true
                        )
                    }
                }
                failure {
                    script {
                        emailext(
                            to: "s2241473112@deakin.edu.au",
                            subject: "Security Scan Failed: ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                            body: "The Security Scan stage of ${env.JOB_NAME} build ${env.BUILD_NUMBER} failed. Please check the attached logs.",
                            attachLog: true
                        )
                    }
                }
            }
        }

        stage("Deploy to Staging") {
            steps {
                script {
                    echo "Deploying the application to the staging environment..."
                    echo "Tool: AWS EC2 instance"
                }
            }
        }

        stage("Integration Tests on Staging") {
            steps {
                script {
                    echo "Running integration tests on the staging environment..."
                    echo "Tool: Newman (Postman CLI)"
                }
            }
        }

        stage("Deploy to Production") {
            steps {
                script {
                    echo "Deploying the application to the production environment..."
                    echo "Tool: AWS EC2 instance"
                }
            }
        }
    }
}