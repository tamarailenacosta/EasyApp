pipeline {
    agent none

    stages {
       
        stage('Vulnerability scan') {
            environment {
                DEBRICKED_CREDENTIALS = credentials('debricked-creds')
                COMMIT = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
            }

            agent {
                docker {
                    image 'debricked/debricked-cli'
                    args '--entrypoint="" -v ${WORKSPACE}:/data -w /data'
                }
            }
            steps {
                sh 'echo $COMMIT'
                sh 'bash /home/entrypoint.sh debricked:scan "$DEBRICKED_CREDENTIALS_USR" "$DEBRICKED_CREDENTIALS_PSW" example-jenkins "$GIT_COMMIT" null cli'
            }
        }
    }
}
