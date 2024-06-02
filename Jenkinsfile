pipeline {
    agent any
    environment {
        GIT_URL = "https://github.com/s223915833/Jenkins-Pipeline.git"
    }
    stages {
        stage('Build') {
            steps {
                echo "fetched the source code from $GIT_URL"
                echo "Building the code with Maven"
                echo "Build completed successfully"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Unit Tests running with JUnit"
                echo "Unit Test completed"
                echo "Integration Tests running with TestNG"
                echo "Integration Test completed"
            }
            post {
                success {
                    emailext to: 'ns.kehelpannala@gmail.com',
                        subject: "Unit and Integration Test Succeeded",
                        body: "Unit and Integration Test succeeded! Please refer attached logs for more details.",
                        attachLog: true
                }
                failure {
                    emailext to: "ns.kehelpannala@gmail.com",
                        subject: "Unit and Integration Test Failed",
                        body: "Unit and Integration Test Failed! Please refer attached logs for more details.",
                        attachLog: true
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Code analysis started with Veracode"
                echo "Code analysis completed successfully"
            }
        }

        stage('Security Scan') {
            steps {
                echo "Code analysis started with OWASP ZAP"
                echo "Code analysis completed successfully"
            }
            post {
                success {
                    emailext to: "ns.kehelpannala@gmail.com",
                        subject: "Security Scan Succeeded",
                        body: "Security Scan succeeded! Please refer attached logs for more details.",
                        attachLog: true
                }
                failure {
                    emailext to: "ns.kehelpannala@gmail.com",
                        subject: "Security Scan Failed",
                        body: "Security Scan Failed! Please refer attached logs for more details.",
                        attachLog: true
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying to staging server, AWS EC2 instance"
                echo "Deployed to AWS EC2 successfully"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Integration tests started with Cypress"
                echo "Integration tests completed successfully"
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying to Production server, AWS EC2 instance"
                echo "Deployed to Production successfully. Server - AWS EC2 instance Test"
            }
        }
    }
}
