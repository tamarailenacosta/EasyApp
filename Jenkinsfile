pipeline {
    agent any
    
    stages {
        stage('see variables') {
            steps {
                sh 'env'
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
                sh 'bash /home/entrypoint.sh debricked:scan "$DEBRICKED_CREDENTIALS_USR" "$DEBRICKED_CREDENTIALS_PSW" "EasyApp" "$GIT_COMMIT" null cli'
            }
        }
        stage('see credencials') {
            steps {
                sh '$DEBRICKED_CREDENTIALS_USR'
            }
        }
    }
    
}
