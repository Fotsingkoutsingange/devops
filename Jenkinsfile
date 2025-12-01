pipeline {
    agent any

    environment {
        // Variables globales si besoin
        APP_NAME = "mon-application"
    }

    stages {

        stage('Checkout') {
            steps {
                echo "📥 Récupération du code..."
                checkout scm
            }
        }

        stage('Installation des dépendances') {
            steps {
                echo "📦 Installation..."
                // Exemple Node.js
                sh 'npm install'
                // Pour Java : sh 'mvn clean install -DskipTests'
                // Pour Python : sh 'pip install -r requirements.txt'
            }
        }

        stage('Tests') {
            steps {
                echo "🧪 Lancement des tests..."
                // Exemple Node.js
                sh 'npm test'
                // Pour Java : sh 'mvn test'
            }
            post {
                always {
                    junit 'tests//*.xml'   // Si tu génères des rapports de tests
                }
            }
        }

        stage('Build / Packaging') {
            steps {
                echo "🏗 Build de l'application..."
                // Exemple Node.js
                sh 'npm run build'
                // Pour Java : sh 'mvn package'
            }
        }

        stage('Archive artifacts') {
            steps {
                echo "📦 Archivage..."
                archiveArtifacts artifacts: 'dist/', fingerprint: true
            }
        }

        stage('Déploiement') {
            when { branch "main" }
            steps {
                echo "🚀 Déploiement en cours..."
                // Met ici ton script de déploiement :
                // sh './deploy.sh'
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline terminé avec succès !"
        }
        failure {
            echo "❌ Pipeline échoué !"
        }
    }
}
