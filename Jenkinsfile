/*
Ejercicio 6
Desarrollar un pipeline que informe lo siguiente:
-	Clima actual
-	Población actual

pipeline
{
    agent any
    
    stages
    {
        stage("Informacion")
        {
            steps
            {
                echo "El clima actual es: Soleado"
                echo "La poblacion actual es de 10000000"
            }
        }
    }
}

/*
Desarrollar un pipeline que genere la siguiente información: 
-	Población neta = población total * 0.8
De su ciudad actual.
La misma se debe almacenar en un archivo plano que se llame “población_neta_fechaActual.txt”
*/
pipeline
{
    agent any
    
    stages
    {
        stage("Poblaciion")
        {
            steps
            {
                script
                {
                    def fecha_hoy = new Date().format("ddMMyyyy")
                    def poblacion_total = 800000
                    def poblacion_neta = poblacion_total * 0.8
                    def string_final = "La poblacion de Barcelona es de: ${poblacion_neta}"
                    writeFile(file:"población_neta_${fecha_hoy}.txt", text: string_final)
                    echo "Se imprimio el archivo."
                }
            }
        }
    }
}
/*
Ejercicio 8:
Leer un fichero de txt que contiene 2 numeros y en base a esos dos números realizar las 4 operaciones aritméticas básicas. 
Fichero: 
100
200

numero1 = 0
numero2 = 0
*/

pipeline
{
    agent any
    
    environment
    {
        ruta = "C:\\Users\\Gusta\\OneDrive\\Documentos\\valores.txt"
    }
    
    stages
    {
        stage("Leo el fichero")
        {
            steps
            {
                script
                {
                    lineas = readFile(file:"${env.ruta}").trim().split("\n")
                    def numero1 = lineas[0].toInteger()
                    def numero2 = lineas[1].toInteger()
                    def suma = numero1+ numero2
                    def resta = numero1- numero2
                    def mult = numero1* numero2
                    def division = numero1 / numero2
                    
                println "Los numeros son: ${numero1} y ${numero2} \nLa suma es: ${suma}, la resta es ${resta}, la multiplicacion es: ${mult} y la division es ${division}"
                }
            }
        }
    }
}
