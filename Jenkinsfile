pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                // Cloner le dépôt Git
                git 'https://github.com/khadythiara/jenkins-build-docker.git'
            }
        }
        
        stage('build image') {
            steps {
                // Construire l'image Docker
                script {
                    def app = docker.build("khady/ngnix")
                }
            }
        }
        
        stage('test image') {
            steps {
                // Tester l'image Docker
                script {
                    docker.image('khady/ngnix').withRun('-p 81:81') { c ->
                        // Vous pouvez ajouter des commandes pour tester l'image ici
                        // Par exemple, utiliser `curl` pour vérifier que le serveur répond
                        sh 'curl -f http://localhost:81 || exit 1'
                    }
                }
            }
        }
    }
    
    post {
        always {
            // Nettoyage ou notifications après l'exécution du pipeline
            echo 'Pipeline terminé.'
        }
    }
}

