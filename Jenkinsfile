pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Build: Fetch the source code from the directory path specified by the environment variable"
                    echo "Build: Compile and package the code using Gradle"
                   // sh 'gradle clean build' ->command to compile and package the code using gradle
                }
            }
            post {
                success {
                    mail to: "nethmini2020.p@gmail.com",
                    subject: "Build Status Email",
                    body: "Gradle build was successful"
                }
                failure {
                    mail to: "nethmini2020.p@gmail.com",
                    subject: "Build Status Email",
                    body: "Gradle build has failed"
                }
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo "Unit and Integration Tests: Run unit tests and integration tests using JUnit gradle tests and integration test"
                    //sh 'gradle test'
                    //sh "gradle integrationTest"
                }
            }
            post {
                //always{
                    //junit '**/build/test-results/test/*.xml' -> Publish JUnit test results
                    //junit '**/build/test-results/integrationTest/*.xml' -> Publish JUnit integration test results}
                success {
                    mail to: "nethmini2020.p@gmail.com",
                    subject: "Test Status Email",
                    body: "Unit and Integration tests were successful"
                }
                failure {
                    mail to: "nethmini2020.p@gmail.com",
                    subject: "Test Status Email",
                    body: "Unit and Integration tests have failed"
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                script {
                    echo "Code Analysis: Analyse the code using PMD to ensure it meets industry standards"
                    //sh 'gradle pmdMain'
                }
            }
            post {
                //always{
                   // pmd pattern: '**build/reports/pmd/*.xml' }
                success {
                    mail to: "nethmini2020.p@gmail.com",
                    subject: "Code Analysis Status Email",
                    body: "Code analysis was successful"
                }
                failure {
                    mail to: "nethmini2020.p@gmail.com",
                    subject: "Code Analysis Status Email",
                    body: "Code analysis has failed"
                }
            }
        }
        
        stage('Security Scan') {
            steps {
                script {
                    echo "Security Scan: Perform a security scan using OWASP Dependency-Check to identify vulnerabilities"
                    //dependencyCheck additionalArguments: '--project "your-project" --scan .', odcInstallation: 'Dependency-Check'
                }
            }
            post {
                //always{
                    //dependencyCheckPublisher pattern: '**/dependency-check-report.xml'}
                success {
                    mail to: "nethmini2020.p@gmail.com",
                    subject: "Security Scan Status Email",
                    body: "Security scan was successful"
                }
                failure {
                    mail to: "nethmini2020.p@gmail.com",
                    subject: "Security Scan Status Email",
                    body: "Security scan has found vulnerabilities!!"
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                script {
                    echo "Deploy to Staging: Deploy the application to a staging server "
                   // sshagent(credentials: [env.SSH_CREDENTIALS_ID]) {
                        //sh """
                        //scp -o StrictHostKeyChecking=no build/libs/your-app.jar user@${env.STAGING_SERVER}:/path/to/deploy/
                       // ssh -o StrictHostKeyChecking=no user@${env.STAGING_SERVER} 'bash -s' < deploy_script.sh
                       // """
                    }
                
                post {    
                    success {
                        mail to: "nethmini2020.p@gmail.com",
                        subject: "Deployment Status",
                        body: "Deployment to staging was successful."
                    }
                    failure {
                        mail to: "nethmini2020.p@gmail.com",
                        subject: "Deployment Status",
                        body: "Deployment to staging failed. Check the Jenkins logs for more details."
                    }
                }
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Integration Tests on Staging: Run integration tests in the staging environment"
                    //sh 'gradle integrationTest'
                }
            }
            post {
                success {
                    mail to: "nethmini2020.p@gmail.com",
                    subject: "Staging Test Status Email",
                    body: "Integration tests on staging were successful"
                }
                failure {
                    mail to: "nethmini2020.p@gmail.com",
                    subject: "Staging Test Status Email",
                    body: "Integration tests on staging have failed"
                }
            }
        }
        
        stage('Deploy to Production') {
            steps {
                script {
                    echo "Deploy to Production: Deploy the application to a production server "
                    // Use SSH to copy the artifacts to the production server
                   // sshagent(credentials: [env.SSH_CREDENTIALS_ID]) {
                       // sh """
                       // scp -o StrictHostKeyChecking=no build/libs/your-app.jar user@${env.PRODUCTION_SERVER}:/path/to/deploy/
                        //sh -o StrictHostKeyChecking=no user@${env.PRODUCTION_SERVER} 'bash -s' < deploy_script.sh
                        //"""
                    }
                }
            
                post {
                    success {
                        mail to: "nethmini2020.p@gmail.com",
                        subject: "Deployment Status Email",
                        body: "Deployment to production was successful"
                    }
                    failure {
                        mail to: "nethmini2020.p@gmail.com",
                        subject: "Deployment Status Email",
                        body: "Deployment to production failed. Check the Jenkins logs for more details."
                    }
                }
            }
        }
    }
}
