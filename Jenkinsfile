pipeline {
    agent any

    stages {
        stage('Scan') {
            steps {
                script {
                    sh 'curl -L https://github.com/debricked/cli/releases/latest/download/cli_linux_x86_64.tar.gz | tar -xz debricked'
                    sh './debricked scan'
                }
            }
        }
    }

    environment {
        DEBRICKED_TOKEN = "$DEBRICKED_TOKEN"
    }
}
