pipeline{
    agent {
        docker{
            image 'mcr.microsoft.com/playwright:v1.60.0-noble'
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