pipeline {
    agent none

    stages {
       
        stage('Vulnerability scan') {
            environment {
                DEBRICKED_TOKEN = credentials('DEBRICKED_TOKEN')
                COMMIT = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
            }

            agent {
                docker {
                    image 'debricked/cli'
                    args '--entrypoint="" -v ${WORKSPACE}:/data -w /data'
                }
            }
            steps {
                sh 'bash /home/entrypoint.sh debricked scan -t "$DEBRICKED_TOKEN" '
            }
        }
    }
}
