pipeline
{
    agent any
    environment 
    {
        numero1 = 1000
        numero2 = 3000
        stringRes = "Resultados: "
        nombre_archivo = "salida_proceso.txt"
    }
    stages
    {
        stage("Suma")
        {
            steps
            {
                script
                {
                    println "El numero 1 es igual a: " + numero1
                    println "El numero 2 es igual a: " + numero2
                    suma = numero1 + numero2
                    println "La suma de los dos numeros es: " + suma
                    stringRes = stringRes + suma + '\n'
                }
            }
        }
        stage("Resta")
        {
            steps
            {
                script
                {
                    resta = numero1 - numero2
                    println "La resta de los dos numeros es: " + resta
                    stringRes = stringRes + resta + '\n'
                    
                }
            }
        }
        stage("Multiplicar")
        {
            steps
            {
                script
                {
                    mul = numero1 * numero2
                    println "La multiplicación de los dos numeros es: " + mul
                    stringRes = stringRes + mul + '\n'
                }
            }
        }
        stage("Dividir")
        {
            steps
            {
                script
                {
                    if (numero2 == 0|| numero1 == 0) {
                        println "Un número no puede dividirse entre 0"
                        div = 0
                        stringRes = stringRes + div + '\n'
                    } else {
                        div = "La divisón de los dos numeros es" + numero2 / numero1
                        println div
                        stringRes = stringRes + div + '\n'
                    }
                }
            }
        }
        stage("Archivo")
        {
            steps
            {
                script
                {
                    writeFile(file: "calculos_" + fechaFormato + ".txt", text: stringRes)
                }
            }
        }
    }
}
