pipeline {
    agent any
    environment {
        API_KEY = 'tu_api_key' // Coloca tu API key aquí si necesitas usar una API de clima
        CITY = 'tu_ciudad' // Cambia esto por tu ciudad
    }
    stages {

        stage('Ejercicio 6 - Clima y Población Actual') {
            steps {
                script {
                    // Para Windows, usamos el comando 'curl' de PowerShell o descarga el curl ejecutable para Windows.
                    def climaUrl = "http://api.openweathermap.org/data/2.5/weather?q=${env.CITY}&appid=${env.API_KEY}&units=metric"
                    def climaResponse = bat(script: "curl ${climaUrl}", returnStdout: true)
                    echo "Clima actual en ${env.CITY}: ${climaResponse}"

                    // Obteniendo población actual desde una API pública o mock (ejemplo con datos ficticios)
                    def poblacionActual = 5000000 // Simula la población o usa una API real
                    echo "Población actual de ${env.CITY}: ${poblacionActual}"
                }
            }
        }

        stage('Ejercicio 7 - Calcular Población Neta') {
            steps {
                script {
                    def poblacionActual = 5000000 // Simula o recupera desde API real
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
                    // Leer archivo que contiene dos números
                    def numeros = readFile('numeros.txt').split('\r\n') // Para Windows, usa '\r\n'
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
