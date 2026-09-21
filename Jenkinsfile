pipeline {
    agent any

    stages {
        stage('Build & Test') {
            steps {
                echo 'Compilando y ejecutando pruebas unitarias...'
                sh 'mvn clean test'
            }
        }
        
        stage('Acceptance Tests') {
            steps {
                echo 'Ejecutando pruebas de aceptación (Acceptance Gates)...'
                sh 'echo "Validación de negocio correcta"'
            }
        }

        stage('Deploy to Staging (Blue-Green)') {
            steps {
                echo 'Iniciando despliegue Blue-Green en ambiente de prueba...'
                sh 'echo "Levantando entorno Green..."'
                sh 'echo "Cambiando tráfico del router a Green..."'
                
                // Simulamos un fallo crítico forzado para demostrar que el Rollback funciona
                sh 'exit 1' 
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline finalizado. Entorno estable.'
        }
        failure {
            echo '===================================='
            echo 'ALERTA: Falla detectada en el entorno Green'
            echo 'Iniciando mecanismo de ROLLBACK...'
            echo 'Revirtiendo tráfico del router al entorno Blue (Estable)'
            echo 'Rollback completado con éxito.'
            echo '===================================='
        }
    }
}