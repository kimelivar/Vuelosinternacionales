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
                // Ejecuta la aplicación en segundo plano
                bat 'start java -jar target\\vuelos-0.0.1-SNAPSHOT.jar'
                // Agrega una espera para no dejar que Jenkins se quede esperando indefinidamente
                sleep(time: 30, unit: 'SECONDS')
            }
        }
    }

    post {
        always {
                echo "No se realizará la limpieza del workspace."
            }
    }
}


