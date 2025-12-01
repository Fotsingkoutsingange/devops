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
                sh 'echo "Build OK"'
            }
        }

        stage('Test') {
            steps {
                echo "🧪 Tests en cours..."
                sh 'echo "Tous les tests sont OK"'
            }
        }

        stage('Deploy') {
            steps {
                echo "🚀 Déploiement fictif réussi"
                sh 'echo "Deploy OK"'
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline terminé SANS ERREUR"
        }
        failure {
            echo "❌ Pipeline échoué — mais normalement impossible ici"
        }
    }
}
