pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Delay') {
            steps {
                script {
                    // Sleep for 1 minute (60 seconds)
                    sleep(time: 60, unit: 'SECONDS')
                }
            }
        }
        stage('Build') {
            steps {
                // Build the code using Maven
                echo "Building the code using Maven"
                // Example:
                // sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests using JUnit and integration tests using Selenium
                echo "Running unit tests and integration tests"
                // Example:
                // sh 'mvn test'
                // sh 'mvn integration-test'
            }
            post {
                success {
                    emailext body: "Unit and Integration Tests passed. No errors found.", subject: "Unit and Integration Tests - Success", to: "inwang197@gmail.com"
                }
                failure {
                    emailext body: "Unit and Integration Tests failed. Please check the attached logs.", subject: "Unit and Integration Tests - Failed", to: "inwang197@gmail.com", attachLog: true
                }
            }
        }
        stage('Code Analysis') {
            steps {
                // Integrate a code analysis tool like SonarQube
                echo "Analyzing code using SonarQube"
                // Example:
                // sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                // Perform security scan using OWASP ZAP or SonarQube
                echo "Performing security scan using OWASP ZAP"
                // Example:
                // sh 'zap-cli --spider <target_url>'
            }
            post {
                success {
                    emailext body: "Unit and Integration Tests passed. No errors found.", subject: "Unit and Integration Tests - Success", to: "inwang197@gmail.com"
                }
                failure {
                    emailext body: "Unit and Integration Tests failed. Please check the attached logs.", subject: "Unit and Integration Tests - Failed", to: "inwang197@gmail.com", attachLog: true
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Deploy application to a staging server (e.g., AWS EC2 instance) using AWS CLI or Ansible
                echo "Deploying application to staging server"
                // Example:
                // sh 'aws s3 sync . s3://staging-bucket'
                // Or using Ansible playbook
                // sh 'ansible-playbook deploy_staging.yml'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on the staging environment
                echo "Running integration tests on staging environment"
                // Example:
                // sh 'mvn verify -Pintegration-tests'
            }
        }
        stage('Deploy to Production') {
            steps {
                // Deploy application to a production server (e.g., AWS EC2 instance) using AWS CLI or Ansible
                echo "Deploying application to production server"
                // Example:
                // sh 'aws s3 sync . s3://production-bucket'
                // Or using Ansible playbook
                // sh 'ansible-playbook deploy_production.yml'
            }
        }
    }
}
