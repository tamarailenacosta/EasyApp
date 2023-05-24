pipeline {

    agent none

    stages {

        stage('Vulnerability scan') {

            environment {

                DEBRICKED_TOKEN = credentials('DEBRICKED_TOKEN')

            }

            agent {

                docker {

                    image 'debricked/debricked-cli'

                    args '--entrypoint="" -v ${WORKSPACE}:/data -w /data'

                }

            }

            steps {

                sh 'bash /home/entrypoint.sh debricked:scan "" "$DEBRICKED_TOKEN" example-jenkins "$GIT_COMMIT" null cli'

            }

        }

    }

}
