pipeline {
    agent any

    stages {

        stage('Start') {
            steps {
                echo "🚀 Pipeline lancé..."
            }
        }

        stage('Build') {
            steps {
                echo "🏗 Étape de build (aucune commande spéciale)"
                bat 'echo Build OK'
            }
        }

        stage('Test') {
            steps {
                echo "🧪 Test en cours..."
                bat 'echo Tests OK'
            }
        }

        stage('Deploy') {
            steps {
                echo "🚀 Déploiement fictif réussi"
                bat 'echo Deploy OK'
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline terminé SANS ERREUR"
        }
        failure {
            echo "❌ Pipeline échoué"
        }
    }
}
