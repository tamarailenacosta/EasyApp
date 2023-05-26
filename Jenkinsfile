pipeline {
    agent none

    stages {
        stage('Vulnerability scan') {
            environment {
                DEBRICKED_TOKEN = credentials('DEBRICKED_TOKEN')
            }
         steps {
                sh '''
                    # Descargar y extraer el binario de Debricked
                    curl -L https://github.com/debricked/cli/releases/latest/download/cli_linux_x86_64.tar.gz | tar -xz
                    cd debricked
                   ./debricked scan
                '''
            }
        }
    }
}

