pipeline {
    agent none

    stages {
        stage('checkout') {
            node('master') {
                steps {
                    sh 'echo $GIT_COMMIT'
                }
            }
        }
        stage('Vulnerability scan') {
            environment {
                DEBRICKED_CREDENTIALS = credentials('debricked-creds')
            }

            agent {
                docker {
                    image 'debricked/debricked-cli'
                    args '--entrypoint="" -v ${WORKSPACE}:/data -w /data'
                }
            }
            steps {
                sh 'echo $GIT_COMMIT'
                sh 'bash /home/entrypoint.sh debricked:scan "$DEBRICKED_CREDENTIALS_USR" "$DEBRICKED_CREDENTIALS_PSW" example-jenkins "$GIT_COMMIT" null cli'
            }
        }
    }
}
