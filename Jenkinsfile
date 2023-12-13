pipeline {
    agent any
    parameters {
        choice(name:'VERSION', choices:['1.0.0','1.1.1','1.2.0'], description: 'Version to deploy on rpod')
        booleanParam(name:'executeTests', defaultValue: true, description:'')

    }
    
    stages {
         stage('Init') {
            steps {
                echo 'Init...'

                // Ajoutez les commandes pour construire votre application ici
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Ajoutez les commandes pour construire votre application ici
            }
        }
        
        stage('Test') {
            when {
                expression {
                    params.executeTests
                }
            }

            steps {
                echo 'Running tests...'
                // Ajoutez les commandes pour exécuter les tests ici
            }
        }
        
        stage('Deploy') { 
            steps {
                echo 'Deploying the application...'
                echo "Deploying version ${params.VERSION}"
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
