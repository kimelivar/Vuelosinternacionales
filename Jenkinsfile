pipeline {
    agent any

    stages {
        stage('Clonar Repositorio') {
            steps {
                // Clona el repositorio de GitHub
                git 'https://github.com/kimelivar/Vuelosinternacionales.git'
            }
        }
        stage('Instalar Dependencias') {
            steps {
                // Instala las dependencias usando Maven Wrapper
                bat '.\\mvnw dependency:resolve'
            }
        }
        stage('Compilar y Construir') {
            steps {
                // Compila el proyecto y genera el archivo JAR
                bat '.\\mvnw clean package'
            }
        }
        stage('Ejecutar Aplicación') {
            steps {
                // Busca y ejecuta el archivo JAR generado
                bat 'java -jar target\\vuelos-0.0.1-SNAPSHOT.jar'
            }
        }
    }

    post {
        always {
            // Limpieza después de la ejecución
            cleanWs()
        }
    }
}

