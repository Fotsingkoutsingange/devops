pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Récupérer le code depuis le dépôt Git
                git branch: 'main', url: 'https://github.com/Fotsingkoutsingange/devops.git'  // Remplacez par l'URL de votre dépôt
            }
        }

        stage('Build') {
            steps {
                // Pour un site statique HTML, aucune compilation n'est nécessaire.
                // Vous pouvez ajouter des étapes comme la validation HTML si souhaité.
                echo 'Aucune étape de build nécessaire pour un site statique.'
            }
        }

        stage('Test') {
            steps {
                // Ajouter des tests simples, comme une validation HTML avec un outil comme htmlhint ou tidy
                sh 'echo "Validation HTML : TODO - Intégrez un outil comme tidy ou htmlhint"'
                // Exemple : sh 'tidy -q -e index.html'  // Si tidy est installé
            }
        }

        stage('Deploy') {
            steps {
                // Déployer les fichiers HTML vers le répertoire d'Apache (assumant un environnement Vagrant avec Apache)
                sh 'sudo cp -r *.html /var/www/html/'  // Copie les fichiers HTML vers le répertoire web
                sh 'sudo systemctl reload apache2'     // Recharger Apache pour appliquer les changements
            }
        }
    }

    post {
        success {
            echo 'Déploiement réussi !'
        }
        failure {
            echo 'Échec du déploiement.'
        }
    }
}
