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
                    app = docker.build("khady/ngnix")
                }
            }
        }
        
        stage('Run Docker Container') {
            steps {
                script {
                    app.run("-d -p 81:81").inside {
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

