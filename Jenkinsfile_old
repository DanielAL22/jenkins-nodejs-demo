pipeline {
    agent any
    
    tools {
        nodejs 'node24' //le dice a Jenkins que instale node24 y modifique automáticamente el PATH
    }


    stages {
        stage('Clonar') {
            steps {
                // Clona el repositorio. Jenkins suele hacerlo automáticamente si el SCm está configurado.
                // Sin embargo, esta es la forma explícita de hacerlo dentro de un Jenkinsfile.
                git branch: 'main', url: 'https://github.com/DanielAL22/jenkins-nodejs-demo.git' // Asegúrate de reemplazar con tu URL real
            }
        }


        stage('Install Dependencies') {
            steps {
                sh 'npm install' // Ejecuta el comando npm install
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test' // Ejecuta el comando npm test
            }
        }
    }

    post {
        // Acciones que se ejecutan después de que todo el pipeline haya terminado
        success {
            echo "🎉 El build fue exitoso"
        }
        failure {
            echo "💥 El build falló"
        }
    }
}