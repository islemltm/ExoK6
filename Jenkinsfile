pipeline {
    agent any

    stages {

        stage('Installer Node.js') {
            steps {
                sh '''
                    apt-get update
                    apt-get install -y nodejs npm

                    node --version
                    npm --version
                '''
            }
        }

        stage('Installer K6') {
            steps {
                sh '''
                    apt-get update
                    apt-get install -y gnupg curl

                    curl -fsSL https://dl.k6.io/key.gpg | gpg --dearmor -o /usr/share/keyrings/k6-archive-keyring.gpg

                    echo "deb [signed-by=/usr/share/keyrings/k6-archive-keyring.gpg] https://dl.k6.io/deb stable main" \
                    > /etc/apt/sources.list.d/k6.list

                    apt-get update
                    apt-get install -y k6

                    k6 version
                '''
            }
        }

        stage('Installer dépendances') {
            steps {
                sh 'npm install'
            }
        }

        stage('Exécuter le test') {
            steps {
                sh 'k6 run k6-script.js'
            }
        }
    }
}
