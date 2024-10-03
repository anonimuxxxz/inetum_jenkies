pipeline {
    agent any

    stages {
        stage('Declarative: Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Operaciones matemáticas') {
            steps {
                script {
                    def a = 10
                    def b = 5
                    def suma = a + b
                    def resta = a - b
                    def multiplicacion = a * b
                    def division = a / b
                    def potencia = Math.pow(a, b)

                    echo "Suma: ${suma}"
                    echo "Resta: ${resta}"
                    echo "Multiplicación: ${multiplicacion}"
                    echo "División: ${division}"
                    echo "Potencia: ${potencia}"

                    // Escribimos los resultados en un archivo
                    writeFile file: 'resultado.txt', text: """Suma: ${suma}
                    Resta: ${resta}
                    Multiplicación: ${multiplicacion}
                    División: ${division}
                    Potencia: ${potencia}"""
                }
            }
        }

        stage('Clonar repositorio') {
            steps {
                git 'https://github.com/anonimuxxxz/inetum_jenkies'
            }
        }

        stage('Ejecutar Maven goals') {
            steps {
                script {
                    echo "Ejecutando tests..."

                    // Verificamos si estamos en Unix o Windows
                    if (isUnix()) {
                        sh 'mvn clean test' // Comando para Unix
                    } else {
                        bat 'mvn clean test' // Comando para Windows
                    }
                }
            }
        }

        stage('Copiar y leer archivo') {
            steps {
                script {
                    // Verificamos si estamos en Unix o Windows para copiar el archivo
                    if (isUnix()) {
                        sh 'cp resultado.txt destino.txt' // Comando Unix
                        sh 'cat destino.txt' // Leer el archivo copiado en Unix
                    } else {
                        bat 'copy resultado.txt destino.txt' // Comando Windows
                        bat 'type destino.txt' // Leer el archivo copiado en Windows
                    }
                }
            }
        }

        stage('Informar usuario') {
            steps {
                echo "¡Pipeline completado correctamente!"
            }
        }
    }

    post {
        always {
            echo 'El pipeline ha finalizado.'
        }
        success {
            echo 'El pipeline fue exitoso.'
        }
        failure {
            echo 'El pipeline ha fallado.'
        }
    }
}
