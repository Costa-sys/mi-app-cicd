pipeline {
    agent any
    tools {
        // Usar las herramientas configuradas en Jenkins
        maven 'Maven3'
        jdk 'JDK17'
    }
    stages {
        stage('Checkout') {
            steps {
                // Obtener el código desde Git
                git 'https://github.com/Costa-sys/mi-app-cicd.git'
            }
        }
        stage('Build') {
            steps {
                // Ejecutar Maven para compilar y empaquetar
                bat 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                // Ejecutar las pruebas unitarias
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
                // Crear el archivo JAR
                bat 'mvn package -DskipTests'
            }
        }
        stage('Deliver') {
            steps {
                // Mostrar mensaje de éxito
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