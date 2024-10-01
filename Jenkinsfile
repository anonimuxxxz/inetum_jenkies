pipeline {
    agent any
    environment {
        CITY = 'Madrid' // Ciudad simulada
    }
    stages {

        stage('Ejercicio 6 - Clima y Población Actual (Simulado)') {
            steps {
                script {
                    // Simulamos el clima y la población
                    def climaSimulado = "Clima soleado, 25°C"
                    def poblacionSimulada = 5000000

                    echo "Clima actual en ${env.CITY} (simulado): ${climaSimulado}"
                    echo "Población actual de ${env.CITY} (simulada): ${poblacionSimulada}"
                }
            }
        }

        stage('Ejercicio 7 - Calcular Población Neta') {
            steps {
                script {
                    def poblacionActual = 5000000 // Simulación de la población
                    def poblacionNeta = poblacionActual * 0.8
                    def fechaActual = new Date().format('yyyy-MM-dd')
                    def nombreFichero = "poblacion_neta_${fechaActual}.txt"

                    writeFile file: nombreFichero, text: "Población neta: ${poblacionNeta}\nFecha: ${fechaActual}"
                    echo "Archivo ${nombreFichero} generado con éxito con la población neta."
                }
            }
        }

        stage('Ejercicio 8 - Operaciones Aritméticas') {
            steps {
                script {
                    // Crear el archivo numeros.txt si no existe
                    writeFile file: 'numeros.txt', text: "100\n200"

                    // Leer el archivo y realizar las operaciones
                    def numeros = readFile('numeros.txt').split('\r\n')
                    def num1 = numeros[0].toInteger()
                    def num2 = numeros[1].toInteger()

                    // Realizar operaciones básicas
                    def suma = num1 + num2
                    def resta = num1 - num2
                    def multiplicacion = num1 * num2
                    def division = num1 / num2

                    echo "Resultados de las operaciones:"
                    echo "Suma: ${suma}"
                    echo "Resta: ${resta}"
                    echo "Multiplicación: ${multiplicacion}"
                    echo "División: ${division}"
                }
            }
        }
    }
}
