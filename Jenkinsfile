pipeline {
  environment {
    imagename = "khadydiagne/ngnix"
    registryCredential = 'simple-java-project'
    dockerImage = ''
  }

    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Construction de l'image Docker
                    dockerImage = docker.build("khady/ngnix")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Exécution du conteneur Docker
                    dockerImage.run("-d -p 8081:80")
                }
            }
        }
      stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push("$BUILD_NUMBER")
             dockerImage.push('latest')

          }
        }
      }
    }  
    }
}

