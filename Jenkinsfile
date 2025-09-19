pipeline {
    agent any

    stages {
        stage('Clonar repositorio') {
            steps {
                git branch: 'main', url: 'https://github.com/jamescanos/jenkins.git'
            }
        }
        stage('Construir contenedor') {
            steps {
                sh 'docker compose build'
            }
        }
        stage('Desplegar') {
            steps {
                sh 'docker compose up -d'
            }
        }
    }
}