pipeline {
    agent none
    
    stages {
        stage('Vulnerability scan') {
            environment {
                DEBRICKED_CREDENTIALS = credentials('debricked-creds')
            }
            steps {
                sh 'echo esto es : $GIT_COMMIT'
                sh 'echo  esto es : "${GIT_COMMIT}" '
                echo "${env.GIT_COMMIT}"
            }

            agent {
                docker {
                    image 'debricked/debricked-cli'
                    args '--entrypoint="" -v ${WORKSPACE}:/data -w /data'
                }
            }
            steps {
               sh 'bash /home/entrypoint.sh debricked:scan $DEBRICKED_CREDENTIALS_USR $DEBRICKED_CREDENTIALS_PSW EasyApp $GIT_COMMIT null cli'
            }
        }
    }
    
}
