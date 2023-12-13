pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Ajoutez les commandes pour construire votre application ici
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Ajoutez les commandes pour exécuter les tests ici
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Ajoutez les commandes pour déployer votre application ici
            }
        }

        stage('Release') {
            steps {
                echo 'Releasing the application...'
                // Ajoutez les commandes pour effectuer la release ici
            }
        }

        stage('Clean') {
            steps {
                echo 'Cleaning up...'
                // Ajoutez les commandes pour nettoyer les artefacts ou effectuer d'autres opérations de nettoyage ici
            }
        }
    }
    
    post {
        always {
            emailext subject: "Pipeline Status: ${currentBuild.result}", 
                      body: "The pipeline status is: ${currentBuild.result}", 
                      to: "maxwell.yeou@manitowoc.com", 
                      attachLog: true
        }
        success {
            echo 'All stages completed successfully. Ready for the next iteration!'
        }
        
        failure {
            echo 'One or more stages failed. Please check the logs for details.'
        }
    }
}
