pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Fetch the source code from the directory path specified by the environment variable that is: ${env.DIRECTORY_PATH}"
                    echo "Compile the code and generate any necessary artifacts"
                }
            }
            post {
                success {
                    mail to: "nethmini2020.p@gmail.com",
                    subject: "Build Status Email",
                    body: "Build was successful"
                }
            }
        }
    }
}
