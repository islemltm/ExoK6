pipeline {
    agent none

    stages {

        stage('Installation dépendances') {
            agent {
                docker {
                    image 'node:22'
                }
            }
            steps {
                sh 'node --version'
                sh 'npm --version'
                sh 'npm install'
            }
        }

        stage('Lancement du test K6') {
            agent {
                docker {
                    image 'grafana/k6'
                }
            }
            steps {
                sh 'k6 version'
                sh 'k6 run k6-script.js'
            }
        }
    }
}
