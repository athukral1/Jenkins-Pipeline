pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "C:\\Users\\ayush\\OneDrive\\Documents\\Y2 T1\\SIT223"
        TESTING_ENVIRONMENT = "Development Environment"
        PRODUCTION_ENVIRONMENT = "Cloud Services"
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from ${env.DIRECTORY_PATH}"
                echo "Compile the code and generate any necessary artifacts"
            }
        }
    
        stage('Test') {
            steps {
                echo "Unit Test"
                echo "Integration Test"
            }
        }

        stage('Code Quality Check') {
            steps {
                echo "Check the quality of the code"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploy the application to a testing environment specified by the ${env.TESTING_ENVIRONMENT}"
            }
        }

        stage('Approval') {
            steps {
                echo "Waiting for manual approval..."
                sleep 10
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploy the code to the ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }
}
