pipeline {
    agent any


    stages {
        stage('Clonar') {
            steps {
                // Clona el repositorio. Jenkins suele hacerlo automáticamente si el SCm está configurado.
                // Sin embargo, esta es la forma explícita de hacerlo dentro de un Jenkinsfile.
                git branch: 'main', url: 'https://github.com/DanielAL22/jenkins-nodejs-demo.git' // Asegúrate de reemplazar con tu URL real
            }
        }

        stage('Use Node.js') {
            steps {
                // Instala la versión de Node.js. Asegúrate de tener el plugin NodeJS instalado en Jenkins.
                tool name: 'node24', type: 'hudson.plugins.nodejs.tools.NodeJsInstallation'
                // 'node24' debe ser el nombre que le diste a tu instalación de Node.js 18 en 'Manage Jenkins -> Global Tool Configuration'.
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