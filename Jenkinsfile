pipeline {
    agent any
    
    stages {
        stage('Build') {
            // Étape de construction
            steps {
                // ...
            }
        }
        
        stage('Test') {
            // Étape de test
            when {
                expression {
                    // Exécute le stage de test seulement sur les branches main, dev et qual
                    return (env.BRANCH_NAME == 'main' || env.BRANCH_NAME == 'dev' || env.BRANCH_NAME == 'qual')
                }
            }
            steps {
                // ...
            }
        }
        
        stage('Deploy') {
            // Étape de déploiement
            when {
                expression {
                    // Exécute le stage de déploiement seulement sur la branche main
                    return (env.BRANCH_NAME == 'main')
                }
            }
            steps {
                // ...
            }
        }
        
        stage('Release') {
            // Étape de release
            when {
                expression {
                    // Exécute le stage de release seulement sur la branche main
                    return (env.BRANCH_NAME == 'main')
                }
            }
            steps {
                // ...
            }
        }
        
        stage('Clean') {
            // Étape de nettoyage
            steps {
                // ...
            }
        }
    }
    
    post {
        success {
            echo 'All stages completed successfully. Ready for the next iteration!'
        }
        
        failure {
            echo 'One or more stages failed. Please check the logs for details.'
        }

        always {
            emailext subject: "Pipeline Status: ${currentBuild.result}", 
                      body: "The pipeline status is: ${currentBuild.result}", 
                      to: "destinataire@example.com", 
                      attachLog: true
        }
    }
}
