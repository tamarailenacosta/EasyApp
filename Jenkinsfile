pipeline {
    agent any
    
   environment {
        DEBRICKED_TOKEN = credentials('DEBRICKED_TOKEN')
    }

    stages {
        stage('Debricked Scan') {
            steps {
                script {
                    sh 'curl -L https://github.com/debricked/cli/releases/latest/download/cli_linux_x86_64.tar.gz | tar -xz debricked'
                    sh './debricked scan'
                }
            }
        }
    }
}
