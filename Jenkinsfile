pipeline {
    agent any

    environment {
        BUILD_AUTOMATION_TOOL = "Maven"
        UNIT_TEST_TOOL = "JUnit"
        INTEGRATION_TEST_TOOL = "Protractor"
        ANALYSE_TOOL = "FindBug"
        SECURITY_SCAN = "Checkmarx"
        SERVER = "AWS EC2 instance"
        DEPLOY_TO_PRODUCTION = ""
    }

    stages {
        stage('Build') {
            steps {
                echo "Build the code using ${env.BUILD_AUTOMATION_TOOL} to compile and package the code."
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Run unit test using ${env.UNIT_TEST_TOOL} to ensure code functions as expected. "
                echo "Run integration test using ${env.INTEGRATION_TEST_TOOL} the different components of the application work together as expected."
            }
            post {
                success {
                    mail to: "ayushithukral0@gmail.com",
                    subject: "Unit and Integration Test Status Email.",
                    body: "Unit and Integration Tests were successful!"
                }
                failure {
                    mail to: "ayushithukral0@gmail.com",
                    subject: "Unit and Integration Test Status Email.",
                    body: "Unit and Integration Tests were unsuccessful!"
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
                echo "Perform a security scan on the code using ${env.SECURITY_SCAN} to identify any vulnerabilities. "
            }
            post {
                success {
                    mail to: "ayushithukral0@gmail.com",
                    subject: "Security Scan Status Email.",
                    body: "Security Scan was successful!"
                }
                failure {
                    mail to: "ayushithukral0@gmail.com",
                    subject: "Security Scan Status Email.",
                    body: "Security Scan was unsuccessful!"
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploy the application to ${env.SERVER}"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Run integration tests on the staging environment to ensure the application functions as expected in a production-like environment. "
            }
            post {
                success {
                    mail to: "ayushithukral0@gmail.com",
                    subject: "Integration Tests on Staging Status Email.",
                    body: "Integration Tests on Staging was successful!"
                }
                failure {
                    mail to: "ayushithukral0@gmail.com",
                    subject: "Integration Tests on Staging Status Email.",
                    body: "Integration Tests on Staging was unsuccessful!"
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploy the application to ${env.SERVER} "
            }
        }
    }
}
