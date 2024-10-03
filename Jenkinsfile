pipeline {
    agent any
    environment {
        FICHERO = "C:\\Users\\antonio.serrano\\valores.txt"  // Ruta al archivo valores.txt
        SALIDA = "C:\\Users\\antonio.serrano\\salida.txt"    // Archivo de salida donde se guardarán los resultados
    }
    stages {
        stage('Lunes - Calcular Poblacion Final') {
            steps {
                script {
                    def lineas = readFile(env.FICHERO).readLines()
                    def valorLinea0 = lineas[0] as Float
                    def calcularPoblacionFinal = valorLinea0 * 0.80
                    echo "Lunes: Población Final calculada: ${calcularPoblacionFinal}"
 
                    // Leer contenido actual del archivo antes de escribir
                    def contenido = fileExists(env.SALIDA) ? readFile(env.SALIDA) : ""
                    contenido += "Lunes: Poblacion Final: ${calcularPoblacionFinal}\n"
                    writeFile file: env.SALIDA, text: contenido
                }
            }
        }
 
        stage('Martes - Operaciones Aritméticas') {
            steps {
                script {
                    def lineas = readFile(env.FICHERO).readLines()
                    def valorLinea1 = lineas[1] as Float
                    def valorLinea2 = lineas[2] as Float
 
                    def suma = valorLinea1 + valorLinea2
                    def resta = valorLinea1 - valorLinea2
                    def multiplicacion = valorLinea1 * valorLinea2
                    def division = valorLinea1 / valorLinea2
 
                    echo "Martes: Suma: ${suma}, Resta: ${resta}, Multiplicación: ${multiplicacion}, División: ${division}"
 
                    def contenido = fileExists(env.SALIDA) ? readFile(env.SALIDA) : ""
                    contenido += "Martes: Suma: ${suma}, Resta: ${resta}, Multiplicación: ${multiplicacion}, División: ${division}\n"
                    writeFile file: env.SALIDA, text: contenido
                }
            }
        }
 
        stage('Miércoles - Convertir Temperatura') {
            steps {
                script {
                    def lineas = readFile(env.FICHERO).readLines()
                    def tempF = lineas[3] as Float
 
                    def tempC = (tempF - 32) * 5 / 9
                    echo "Miércoles: Temperatura en Celsius: ${tempC}"
 
                    def contenido = fileExists(env.SALIDA) ? readFile(env.SALIDA) : ""
                    contenido += "Miércoles: Temperatura en Celsius: ${tempC}\n"
                    writeFile file: env.SALIDA, text: contenido
                }
            }
        }
 
        stage('Jueves - Informar Usuario') {
            steps {
                script {
                    // Ejecutar comando en Windows usando 'bat' en lugar de 'sh'
                    def usuario = bat(script: 'whoami', returnStdout: true).trim()
                   echo "El usuario del PC es: ${env.USERNAME}" // Esto mostrará el nombre de usuario
 
                    def contenido = fileExists(env.SALIDA) ? readFile(env.SALIDA) : ""
                    contenido += "Jueves: Usuario que ejecuta el pipeline: ${usuario}\n"
                    writeFile file: env.SALIDA, text: contenido
                }
            }
        }
 
              stage('Viernes - Crear Proyecto Maven') {
            steps {
                script {
                    // Descargar el proyecto básico de Maven y compilarlo
                    bat '''
                    curl -o project.zip https://start.spring.io/starter.zip ^
                        -d dependencies=mysql ^
                        -d type=maven-project ^
                        -d language=java ^
                        -d packaging=jar ^
                        -d javaVersion=11
            
                    powershell -Command "Expand-Archive -Path 'project.zip' -DestinationPath '.'"
                    cd proyecto_maven
                    mvn clean install
                    '''
                    echo "Viernes: Proyecto Maven creado y compilado con éxito"
                }
            }
        }
    }
    post {
        always {
            script {
                echo "Pipeline completado. Revisa el archivo ${env.SALIDA} para los resultados."
            }
        }
    }
}
