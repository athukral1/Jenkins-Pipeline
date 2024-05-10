pipeline {
    agent any

    environment {
        BUILD_AUTOMATION_TOOL = "Maven"
        UNIT_TEST_TOOL = "JUnit"
        INTEGRATION_TEST_TOOL = "Protractor"
        ANALYSE_TOOL = "FindBug"
        SECURITY_SCAN = "Checkmarx"
        SERVER = "AWS EC2 instance"
    }

    stages {
        stage('Build') {
            steps {
                echo "Build the code using ${env.BUILD_AUTOMATION_TOOL} to compile and package the code."
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Run unit test using ${env.UNIT_TEST_TOOL} to ensure code functions as expected."
                echo "Run integration test using ${env.INTEGRATION_TEST_TOOL} the different components of the application work together as expected."
            }
            post {
                success {
                    emailext attachmentsPattern: 'logs/*.log',
                             body: "Unit and Integration Tests were successful!",
                             subject: "Unit and Integration Test Status Email.",
                             to: "ayushithukral0@gmail.com"
                }
                failure {
                    emailext attachmentsPattern: 'logs/*.log',
                             body: "Unit and Integration Tests were unsuccessful!",
                             subject: "Unit and Integration Test Status Email.",
                             to: "ayushithukral0@gmail.com"
                }
            }
        }

        stage('Code Check') {
            steps {
                echo "Use ${env.ANALYSE_TOOL} to analyse the code and ensure it meets industry standards."
            }
        }

        stage('Security Scan') {
            steps {
                echo "Perform a security scan on the code using ${env.SECURITY_SCAN} to identify any vulnerabilities."
            }
            post {
                success {
                    emailext attachmentsPattern: 'logs/*.log',
                             body: "Security Scan was successful!",
                             subject: "Security Scan Status Email.",
                             to: "ayushithukral0@gmail.com"
                }
                failure {
                    emailext attachmentsPattern: 'logs/*.log',
                             body: "Security Scan was unsuccessful!",
                             subject: "Security Scan Status Email.",
                             to: "ayushithukral0@gmail.com"
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploy the application to ${env.SERVER}"
                sleep 10
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Run integration tests on the staging environment to ensure the application functions as expected in a production-like environment."
            }
            post {
                success {
                    emailext attachmentsPattern: 'logs/*.log',
                             body: "Integration Tests on Staging were successful!",
                             subject: "Integration Tests on Staging Status Email.",
                             to: "ayushithukral0@gmail.com"
                }
                failure {
                    emailext attachmentsPattern: 'logs/*.log',
                             body: "Integration Tests on Staging were unsuccessful!",
                             subject: "Integration Tests on Staging Status Email.",
                             to: "ayushithukral0@gmail.com"
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploy the application to ${env.SERVER}"
            }
        }
    }
}
