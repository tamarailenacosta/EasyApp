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
                   // args '--entrypoint=""'
                }
            }
            steps {
                sh " debricked scan // -t ${DEBRICKED_TOKEN}"  Update the command to use environment variable
            }
        }
    }
}

