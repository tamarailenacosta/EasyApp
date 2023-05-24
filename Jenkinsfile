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
                    image 'debricked/debricked-cli'
                    //args '--entrypoint="" -v ${WORKSPACE}:/data -w /data'
                }
            }
            steps {
                sh 'docker run -v $(pwd):/root debricked/cli:scan -t "$DEBRICKED_TOKEN"''
            }
        }
    }
}
