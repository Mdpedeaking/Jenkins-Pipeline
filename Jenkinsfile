pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Build: Fetch the source code from the directory path specified by the environment variable"
                    echo "Build: Compile and package the code using Gradle"
                    // sh 'gradle clean build' -> command to compile and package the code using gradle
                }
            }
            post {
                success {
                    emailext attachLog: true, 
                             subject: "Build Status - SUCCESS", 
                             body: "Gradle build was successful", 
                             to: 'nethmini2020.p@gmail.com'
                }
                failure {
                    emailext attachLog: true, 
                             subject: "Build Status - FAILURE", 
                             body: "Gradle build has failed", 
                             to: 'nethmini2020.p@gmail.com'
                }
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo "Unit and Integration Tests: Run unit tests and integration tests using JUnit gradle tests and integration test"
                    // sh 'gradle test'
                    // sh "gradle integrationTest"
                }
            }
            post {
                always {
                    emailext attachLog: true, 
                             subject: "Unit and Integration Test Logs", 
                             body: "Attached are the logs for unit and integration tests.", 
                             to: 'nethmini2020.p@gmail.com'
                }
                success {
                    emailext attachLog: true, 
                             subject: "Test Status - SUCCESS", 
                             body: "Unit and Integration tests were successful", 
                             to: 'nethmini2020.p@gmail.com'
                }
                failure {
                    emailext attachLog: true, 
                             subject: "Test Status - FAILURE", 
                             body: "Unit and Integration tests have failed", 
                             to: 'nethmini2020.p@gmail.com'
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                script {
                    echo "Code Analysis: Analyse the code using PMD to ensure it meets industry standards"
                    // sh 'gradle pmdMain'
                }
            }
            post {
                always {
                    emailext attachLog: true, 
                             subject: "Code Analysis Logs", 
                             body: "Attached are the logs for code analysis.", 
                             to: 'nethmini2020.p@gmail.com'
                }
                success {
                    emailext attachLog: true, 
                             subject: "Code Analysis Status - SUCCESS", 
                             body: "Code analysis was successful", 
                             to: 'nethmini2020.p@gmail.com'
                }
                failure {
                    emailext attachLog: true, 
                             subject: "Code Analysis Status - FAILURE", 
                             body: "Code analysis has failed", 
                             to: 'nethmini2020.p@gmail.com'
                }
            }
        }
        
        stage('Security Scan') {
            steps {
                script {
                    echo "Security Scan: Perform a security scan using OWASP Dependency-Check to identify vulnerabilities"
                    // dependencyCheck additionalArguments: '--project "your-project" --scan .', odcInstallation: 'Dependency-Check'
                }
            }
            post {
                always {
                    emailext attachLog: true, 
                             subject: "Security Scan Logs", 
                             body: "Attached are the logs for the security scan.", 
                             to: 'nethmini2020.p@gmail.com'
                }
                success {
                    emailext attachLog: true, 
                             subject: "Security Scan Status - SUCCESS", 
                             body: "Security scan was successful", 
                             to: 'nethmini2020.p@gmail.com'
                }
                failure {
                    emailext attachLog: true, 
                             subject: "Security Scan Status - FAILURE", 
                             body: "Security scan has found vulnerabilities!!", 
                             to: 'nethmini2020.p@gmail.com'
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                script {
                    echo "Deploy to Staging: Deploy the application to a staging server"
                    // sshagent(credentials: [env.SSH_CREDENTIALS_ID]) {
                    //     sh """
                    //     scp -o StrictHostKeyChecking=no build/libs/your-app.jar user@${env.STAGING_SERVER}:/path/to/deploy/
                    //     ssh -o StrictHostKeyChecking=no user@${env.STAGING_SERVER} 'bash -s' < deploy_script.sh
                    //     """
                    // }
                }
            }
            post {
                always {
                    emailext attachLog: true, 
                             subject: "Deployment to Staging Logs", 
                             body: "Attached are the logs for deployment to staging.", 
                             to: 'nethmini2020.p@gmail.com'
                }
                success {
                    emailext attachLog: true, 
                             subject: "Deployment Status - SUCCESS", 
                             body: "Deployment to staging was successful", 
                             to: 'nethmini2020.p@gmail.com'
                }
                failure {
                    emailext attachLog: true, 
                             subject: "Deployment Status - FAILURE", 
                             body: "Deployment to staging failed. Check the Jenkins logs for more details.", 
                             to: 'nethmini2020.p@gmail.com'
                }
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Integration Tests on Staging: Run integration tests in the staging environment"
                    // sh 'gradle integrationTest'
                }
            }
            post {
                always {
                    emailext attachLog: true, 
                             subject: "Staging Integration Test Logs", 
                             body: "Attached are the logs for integration tests on staging.", 
                             to: 'nethmini2020.p@gmail.com'
                }
                success {
                    emailext attachLog: true, 
                             subject: "Staging Test Status - SUCCESS", 
                             body: "Integration tests on staging were successful", 
                             to: 'nethmini2020.p@gmail.com'
                }
                failure {
                    emailext attachLog: true, 
                             subject: "Staging Test Status - FAILURE", 
                             body: "Integration tests on staging have failed", 
                             to: 'nethmini2020.p@gmail.com'
                }
            }
        }
        
        stage('Deploy to Production') {
            steps {
                script {
                    echo "Deploy to Production: Deploy the application to a production server"
                    // sshagent(credentials: [env.SSH_CREDENTIALS_ID]) {
                    //     sh """
                    //     scp -o StrictHostKeyChecking=no build/libs/your-app.jar user@${env.PRODUCTION_SERVER}:/path/to/deploy/
                    //     ssh -o StrictHostKeyChecking=no user@${env.PRODUCTION_SERVER} 'bash -s' < deploy_script.sh
                    //     """
                    // }
                }
            }
            post {
                always {
                    emailext attachLog: true, 
                             subject: "Deployment to Production Logs", 
                             body: "Attached are the logs for deployment to production.", 
                             to: 'nethmini2020.p@gmail.com'
                }
                success {
                    emailext attachLog: true, 
                             subject: "Deployment Status - SUCCESS", 
                             body: "Deployment to production was successful", 
                             to: 'nethmini2020.p@gmail.com'
                }
                failure {
                    emailext attachLog: true, 
                             subject: "Deployment Status - FAILURE", 
                             body: "Deployment to production failed. Check the Jenkins logs for more details.", 
                             to: 'nethmini2020.p@gmail.com'
                }
            }
        }
    }
}

