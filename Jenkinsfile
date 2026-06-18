pipeline{
    agent {
        docker{
            image 'grafana/k6'
        }
    }
    stages{
        
        stage("installation dépendances"){
            steps{
                sh'node --version'
                sh'npm install'
            }
        }

        stage("Lancement du test"){
            steps{
                sh'k6 run k6-script.js'
            }
        }
    }
}