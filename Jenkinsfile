pipeline {
    agent any

    stages {
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
                // Transférer les fichiers HTML vers la VM Vagrant via SSH
                sshPublisher(
                    publishers: [
                        sshPublisherDesc(
                            configName: 'Vagrant-VM',  // Nom de la config SSH définie dans Jenkins
                            transfers: [
                                sshTransfer(
                                    sourceFiles: '*.html',  // Fichiers à transférer depuis le workspace
                                    remoteDirectory: '/var/www/html/',  // Répertoire cible sur la VM (Apache)
                                    execCommand: 'sudo systemctl reload apache2'  // Recharger Apache après transfert
                                )
                            ]
                        )
                    ]
                )
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
