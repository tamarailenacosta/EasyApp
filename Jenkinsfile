pipeline {
    agent none
    
    stages {
        stage('see variables') {
            steps {
                sh 'env'
            }
        }
    }
    stages {
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
                sh 'bash /home/entrypoint.sh debricked:scan "$DEBRICKED_CREDENTIALS_USR" "$DEBRICKED_CREDENTIALS_PSW" "EasyApp" "$GIT_COMMIT" null cli'
            }
        }
    }
}
