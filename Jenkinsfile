pipeline {
    agent none

    stages {
       
        stage('Vulnerability scan') {
            environment {
                COMMIT = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
            }

            agent {
                docker {
                    image 'debricked/debricked-cli'
                    args '--entrypoint="" -v ${WORKSPACE}:/data -w /data'
                }
            }
            steps {
                sh 'echo este es el contenido del : $COMMIT'
                sh 'echo este es el segundo commit: $GIT_COMMIT'
                sh 'bash /home/entrypoint.sh debricked:scan "" "$DEBRICKED_TOKEN" example-jenkins "$COMMIT" null cli'
            }
        }
    }
}
