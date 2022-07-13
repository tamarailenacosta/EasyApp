pipeline {
    agent any
    
    stages {
        stage('Vulnerability scan') {
            environment {
                DEBRICKED_CREDENTIALS = credentials('debricked-creds')
            }
            steps {
                sh 'echo esto es 1: $GIT_COMMIT'
                sh 'echo  esto es 2: "$GIT_COMMIT" '
                sh 'echo esto es 3: $DEBRICKED_CREDENTIALS_USR'
                sh 'echo git rev-parse HEAD'
            }

            /*agent {
                docker {
                    image 'debricked/debricked-cli'
                    args '--entrypoint="" -v ${WORKSPACE}:/data -w /data'
                }
            }
            steps {
               sh 'bash /home/entrypoint.sh debricked:scan $DEBRICKED_CREDENTIALS_USR $DEBRICKED_CREDENTIALS_PSW EasyApp $GIT_COMMIT null cli'
            }*/
        }
    }
    
}
