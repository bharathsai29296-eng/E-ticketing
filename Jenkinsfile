pipeline {
    agent any

    tools {
        maven 'MAVEN-HOME'
    }

    stages {

        stage('Clean') {
            steps {
                bat 'mvn clean'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn install'
            }
        }
    }

    post {

        success {
            emailext(
                to: 'bharathkalva29296@gmail.com',
                subject: "BUILD SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
Hello,

Your Jenkins build completed successfully!

Job Name: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Build Status: SUCCESS

Build URL: ${env.BUILD_URL}

Regards,
Jenkins CI/CD
"""
            )
        }

        failure {
            emailext(
                to: 'bharathkalva29296@gmail.com',
                subject: "BUILD FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
Hello,

Your Jenkins build has FAILED!

Job Name: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Build Status: FAILURE

Please check the Jenkins console output to identify the error.

Build URL: ${env.BUILD_URL}

Regards,
Jenkins CI/CD
"""
            )
        }

    }
}
