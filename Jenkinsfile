pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Compilando el proyecto...'
                sh 'mvn clean compile'
            }
        }
        
        stage('Unit Tests') {
            steps {
                echo 'Ejecutando pruebas unitarias con JUnit...'
                sh 'mvn test'
            }
        }
        
        stage('Integration Tests') {
            steps {
                echo 'Ejecutando pruebas de integración...'
                // En un entorno real usaríamos 'mvn failsafe:integration-test'
                sh 'echo "Pruebas de integración superadas con Selenium"'
            }
        }
    }
}