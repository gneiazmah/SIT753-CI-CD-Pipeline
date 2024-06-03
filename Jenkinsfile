pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "C:\\Users\\hp\\Desktop\\753\\Task 6\\SIT753-CI-CD-Pipeline"
        TESTING_ENVIRONMENT = "Testing Environment"
        PRODUCTION_ENVIRONMENT = "Gnei Azmah"
        EMAIL_RECIPIENT = "96az.ma@gmail.com"
    }

    stages {
        stage('Build') {
            steps {
                echo "Building the code using Maven"
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests with JUnit"
                echo "Running integration tests with JUnit"
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo "Analyzing code with SonarQube"
            }
        }
        
        stage('Security Scan') {
            steps {
                echo "Performing security scan with OWASP Dependency Check"
            }
            post {
                always {
                    script {
                        emailext(
                            to: "${env.EMAIL_RECIPIENT}",
                            subject: "Security Scan Results",
                            body: "Security scan completed with status: ${currentBuild.currentResult}",
                            attachLog: true
                        )
                    }
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to ${env.TESTING_ENVIRONMENT}"
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on ${env.TESTING_ENVIRONMENT}"
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo "Deploying the code to the production environment ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }

    post {
        success {
            script {
                emailext(
                    to: "${env.EMAIL_RECIPIENT}",
                    subject: "Pipeline Success",
                    body: "Pipeline completed successfully.",
                    attachLog: true
                )
            }
        }
        failure {
            script {
                emailext(
                    to: "${env.EMAIL_RECIPIENT}",
                    subject: "Pipeline Failed",
                    body: "Pipeline failed. Please check the logs.",
                    attachLog: true
                )
            }
        }
    }
}
