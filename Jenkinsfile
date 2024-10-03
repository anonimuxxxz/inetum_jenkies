pipeline {
    agent any

    environment {
        // Definir las variables globales necesarias
        CLONE_URL = "https://github.com/anonimuxxxz/inetum_jenkies"
        BRANCH = "main"
        OUTPUT_FILE = "output.txt"
    }

    stages {
        stage('Día Lunes - Operaciones matemáticas') {
            when { expression { return isDayOfWeek('Monday') } }
            steps {
                script {
                    def num1 = 10
                    def num2 = 5

                    // Realizar operaciones matemáticas
                    def suma = num1 + num2
                    def resta = num1 - num2
                    def multiplicacion = num1 * num2
                    def division = num1 / num2
                    def potencia = Math.pow(num1, num2)

                    // Mostrar resultados en consola
                    echo "Suma: ${suma}"
                    echo "Resta: ${resta}"
                    echo "Multiplicación: ${multiplicacion}"
                    echo "División: ${division}"
                    echo "Potencia: ${potencia}"

                    // Generar un archivo con la información del día lunes
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

        stage('Día Martes - Clonar repositorio') {
            when { expression { return isDayOfWeek('Tuesday') } }
            steps {
                // Clonar el repositorio de la rama principal
                git branch: "${BRANCH}", url: "${CLONE_URL}"
            }
        }

        stage('Día Miércoles - Ejecutar Maven goals') {
            when { expression { return isDayOfWeek('Wednesday') } }
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

        stage('Día Jueves - Copiar y leer archivo generado el Miércoles') {
            when { expression { return isDayOfWeek('Thursday') } }
            steps {
                script {
                    // Copiar el archivo generado el día miércoles
                    def destination = 'copied_output.txt'
                    sh "cp ${OUTPUT_FILE} ${destination}"

                    // Leer el archivo y mostrar su contenido en consola
                    def fileContent = readFile(destination)
                    echo "Contenido del archivo copiado:\n${fileContent}"
                }
            }
        }

        stage('Día Viernes - Informar usuario que ejecutó la tarea') {
            when { expression { return isDayOfWeek('Friday') } }
            steps {
                script {
                    def user = sh(script: "whoami", returnStdout: true).trim()
                    echo "Tarea ejecutada por el usuario: ${user}"
                }
            }
        }
    }
}

def isDayOfWeek(day) {
    def currentDay = new Date().format('EEEE', TimeZone.getTimeZone('GMT'))
    return currentDay == day
}
