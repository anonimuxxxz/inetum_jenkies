pipeline {
    agent any
    environment {
        // Simulación de los datos que no se pueden obtener mediante APIs
        CLIMA_ACTUAL = "Despejado, 25°C"
        POBLACION_ACTUAL = 5000000 // Ejemplo de población actual
    }
    stages {
        stage('Ejercicio 6: Informar Clima y Población Actual') {
            steps {
                script {
                    echo "===== Clima Actual ====="
                    echo "Clima: ${env.CLIMA_ACTUAL}"
                    echo "===== Población Actual ====="
                    echo "Población: ${env.POBLACION_ACTUAL}"
                }
            }
        }
        stage('Ejercicio 7: Calcular Población Neta') {
            steps {
                script {
                    def poblacionTotal = env.POBLACION_ACTUAL.toInteger()
                    def poblacionNeta = poblacionTotal * 0.8
                    def fechaActual = new Date().format('yyyy-MM-dd')

                    // Crear archivo con la población neta
                    def archivoNombre = "poblacion_neta_${fechaActual}.txt"
                    writeFile file: archivoNombre, text: "Población neta (80% de la población total): ${poblacionNeta}"

                    // Mostrar información en consola
                    echo "===== Población Neta ====="
                    echo "Población neta calculada: ${poblacionNeta}"
                    echo "Archivo generado: ${archivoNombre}"
                }
            }
        }
    }
    post {
        success {
            echo 'Pipeline completado exitosamente.'
        }
        failure {
            echo 'Hubo un error en el pipeline.'
        }
    }
}
