pipeline {
    agent any
    tools {
        maven 'Maven3'
        jdk 'JDK17'
    }
    stages {
        // Quitamos la etapa 'Checkout' manual para evitar el error de ramas
        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
        stage('Package') {
            steps {
                bat 'mvn package -DskipTests'
            }
        }
        stage('Deliver') {
            steps {
                echo 'Aplicación empaquetada y lista para desplegar.'
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}