pipeline {
    agent any

    stages {
        stage('Clonar repositorio') {
            steps {
                git branch: 'main', url: 'https://github.com/jamescanos/cloudcomputing.git'
            }
        }
        stage('Construir contenedor') {
            steps {
                sh 'docker build -t cloudcomputing .'
            }
        }
        stage('Desplegar') {
            steps {
                sh 'docker run -d -p 8090:80 cloudcomputing'
            }
        }
    }
}
