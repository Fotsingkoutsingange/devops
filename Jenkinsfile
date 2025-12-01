pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Récupérer le code depuis le dépôt Git
                git branch: 'main', url: 'https://github.com/Fotsingkoutsingange/devops.git'
            }
        }

        stage('Build') {
            steps {
                // Pour un site statique HTML, aucune compilation n'est nécessaire.
                echo 'Aucune étape de build nécessaire pour un site statique.'
            }
        }

        stage('Test') {
            steps {
                // Utiliser bat au lieu de sh pour Windows
                bat 'echo Validation HTML : TODO - Intégrez un outil comme tidy ou htmlhint'
                // Exemple pour Windows : bat 'tidy -q -e index.html' si tidy est installé
            }
        }

        stage('Deploy') {
            steps {
                // Pour Windows, ajuster les commandes. Si le déploiement est sur une VM Linux (Vagrant), utilisez un agent approprié ou SSH.
                // Ici, assumant un environnement Windows avec Apache installé (rare), ou ajustez pour votre setup.
                // Si Apache est sur une VM, remplacez par des commandes Windows ou utilisez un plugin comme SSH.
                bat 'copy *.html C:\\Apache24\\htdocs\\'  // Exemple pour Apache sur Windows (ajustez le chemin)
                bat 'net stop Apache2.4 && net start Apache2.4'  // Redémarrer Apache sur Windows
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
