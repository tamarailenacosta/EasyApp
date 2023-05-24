pipeline {
    agent none

    stages {
        stage('Vulnerability scan') {
            environment {
                DEBRICKED_TOKEN = credentials('DEBRICKED_TOKEN')
            }
            agent {
                docker {
                    image 'debricked/cli'
                    args '--entrypoint=""' // Remove the commented out section
                }
            }
            steps {
                sh "docker run -v ${WORKSPACE}:/root debricked/cli:scan -t ${DEBRICKED_TOKEN}" // Update the command to use environment variable
            }
        }
    }
}

