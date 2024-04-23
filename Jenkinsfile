pipeline {
    agent any
    
    environment {
        DIRECTORY_PATH = '/Users/tina/Documents/GitHub/753_pipeline'
        TESTING_ENVIRONMENT = 'testing_environment'
        PRODUCTION_ENVIRONMENT = 'production_environment'
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Fetching the source code from the directory path specified by the environment variable: ${env.DIRECTORY_PATH}"
                echo "Compiling the code and generating any necessary artifacts"
            }
            post{
                success{
                    mail to: "tienht.vn@gmail.com",
                    subject: "Build Status Email",
                    body: "Build was successful!"
                }
            }
        }
        stage('Test') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
            }
        }
        stage('Code Quality Check') {
            steps {
                echo "Checking the quality of the code"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying the application to a testing environment specified by the environment variable: ${env.TESTING_ENVIRONMENT}"
            }
        }
        stage('Approval') {
            steps {
                echo "Waiting for manual approval..."
                script {
                    sleep time: 10, unit: 'SECONDS'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying code to the production environment (${env.PRODUCTION_ENVIRONMENT})"
            }
        }
    }
}
