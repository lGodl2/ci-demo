pipeline {
    agent any

    stages {
        stage('Clonar') {
            steps {
                git 'https://github.com/TU_USUARIO/ci-demo.git'
            }
        }

        stage('Construir Imagen Docker') {
            steps {
                sh 'docker build -t ci-demo-app .'
            }
        }

        stage('Probar Contenedor') {
            steps {
                sh 'docker run -d -p 5000:5000 --name ci-demo-test ci-demo-app'
                sh 'sleep 5 && curl http://localhost:5000'
            }
        }

        stage('Limpiar') {
            steps {
                sh 'docker rm -f ci-demo-test || true'
                sh 'docker rmi ci-demo-app || true'
            }
        }
    }
}
