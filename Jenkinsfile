pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Tests multiversión') {
            parallel {
                stage('Node 20') {
                    agent { label 'any' }
                    tools {
                        nodejs 'node20'
                    }
                    steps {
                        sh 'node -v'
                        sh 'npm install'
                        sh 'npm test'
                    }
                }

                // stage('Node 22') {
                //     agent { label 'any' }
                //     tools {
                //         nodejs 'node22'
                //     }
                //     steps {
                //         sh 'node -v'
                //         sh 'npm install'
                //         sh 'npm test'
                //     }
                // }

                // stage('Node 24') {
                //     agent { label 'any' }
                //     tools {
                //         nodejs 'node24'
                //     }
                //     steps {
                //         sh 'node -v'
                //         sh 'npm install'
                //         sh 'npm test'
                //     }
                // }
            }
        }
    }

    post {
        success {
            echo "✅ Tests exitosos en todas las versiones"
        }
        failure {
            echo "❌ Al menos una versión falló"
        }
    }
}
