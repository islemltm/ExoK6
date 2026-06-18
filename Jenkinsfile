pipeline {
    agent {
        docker {
            image 'node:22'
        }
    }

    stages {

        stage('Installation dépendances') {
            steps {
                sh 'node --version'
                sh 'npm --version'
                sh 'npm install'
            }
        }

        stage('Lancement du test K6') {
            steps {
                sh '''
                    docker run --rm \
                    -v $WORKSPACE:/scripts \
                    grafana/k6 run /scripts/k6-script.js
                '''
            }
        }
    }
}
