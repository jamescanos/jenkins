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
                # Si existe un contenedor llamado jenkins, lo elimina antes de crear uno nuevo
                if [ "$(docker ps -aq -f name=jenkins)" ]; then
                    echo "Eliminando contenedor existente..."
                    docker rm -f jenkins || true
                fi

                docker compose up -d
                '''
            }
        }
    }
}
