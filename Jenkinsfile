pipeline {
    agent any

    environment {
        CLONE_URL = "https://github.com/anonimuxxxz/inetum_jenkies"
        BRANCH = "main"
        OUTPUT_FILE = "output.txt"
    }

    stages {
        stage('Operaciones matemáticas') {
            steps {
                script {
                    def num1 = 10
                    def num2 = 5

                    // Realizar operaciones matemáticas
                    def suma = num1 + num2
                    def resta = num1 - num2
                    def multiplicacion = num1 * num2
                    def division = num1 / num2
                    def potencia = num1 ** num2 // Cambiado aquí

                    // Mostrar resultados en consola
                    echo "Suma: ${suma}"
                    echo "Resta: ${resta}"
                    echo "Multiplicación: ${multiplicacion}"
                    echo "División: ${division}"
                    echo "Potencia: ${potencia}"

                    // Generar un archivo con la información
                    writeFile file: "${OUTPUT_FILE}", text: """
                        Operaciones matemáticas:
                        Suma: ${suma}
                        Resta: ${resta}
                        Multiplicación: ${multiplicacion}
                        División: ${division}
                        Potencia: ${potencia}
                    """
                }
            }
        }

        stage('Clonar repositorio') {
            steps {
                // Clonar el repositorio de la rama principal
                git branch: "${BRANCH}", url: "${CLONE_URL}"
            }
        }

        stage('Ejecutar Maven goals') {
            steps {
                script {
                    // Ejecutar los tests
                    echo "Ejecutando tests..."
                    sh "mvn test"

                    // Ejecutar los goals clean e install
                    echo "Ejecutando clean e install..."
                    sh "mvn clean install"
                }
            }
        }

        stage('Copiar y leer archivo') {
            steps {
                script {
                    // Copiar el archivo generado
                    def destination = 'copied_output.txt'
                    sh "cp ${OUTPUT_FILE} ${destination}"

                    // Leer el archivo y mostrar su contenido en consola
                    def fileContent = readFile(destination)
                    echo "Contenido del archivo copiado:\n${fileContent}"
                }
            }
        }

        stage('Informar usuario') {
            steps {
                script {
                    def user = sh(script: "AntnioSerrano", returnStdout: true).trim()
                    echo "Tarea ejecutada por el usuario: ${user}"
                }
            }
        }
    }
}
