pipeline {
    agent any

    stages {
        // Supprimez cette étape si elle est redondante avec la déclarative
        // stage('Checkout') {
        //     steps {
        //         git branch: 'main', url: 'https://github.com/Fotsingkoutsingange/devops.git'
        //     }
        // }

        stage('Build') {
            steps {
                echo 'Aucune étape de build nécessaire pour un site statique.'
            }
        }

        stage('Test') {
            steps {
                bat 'echo Validation HTML : TODO - Intégrez un outil comme tidy ou htmlhint'
            }
        }

        stage('Deploy') {
            steps {
                bat 'copy *.html C:\\Apache24\\htdocs\\'
                bat 'net stop Apache2.4 && net start Apache2.4'
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
