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
                sh '''
                if [ "$(docker ps -aq -f name=jenkins-app)" ]; then
                    echo "Eliminando contenedor jenkins-app existente..."
                    docker rm -f jenkins-app || true
                fi

                docker compose up -d
                '''
            }
        }
    }
}
