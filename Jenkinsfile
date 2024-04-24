def stringRes = "Resultados: "
pipeline
{
    agent any
    environment 
    {
        numero1 = 1000
        numero2 = 3000
        nombre_archivo = "salida_proceso.txt"
    }
    options
    {
        timeout(time:10, unit: "MINUTES")
        quietPeriod(10)
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }
    stages
    {
        stage("1")
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
                    resta = numero1 - numero2
                    println "La resta de los dos numeros es: " + resta
                    stringRes = stringRes + resta + '\n'
                    mul = numero1 * numero2
                    println "La multiplicacion de los dos numeros es: " + mul
                    stringRes = stringRes + mul + '\n'
                    if (numero2 == 0 || numero1 == 0) {
                        println "Un numero no puede dividirse entre 0"
                        div = 0
                        stringRes = stringRes + div + '\n'
                    } else {
                        div = numero2 / numero1
                        println "La division de los dos numeros es: " + resta
                        stringRes = stringRes + div + '\n'
                    }
                }
            }
        }
        stage("2")
        {
            steps
            {
                bat "ipconfig /flushdns"
            }
        }
        stage("3")
        {
            steps
            {
                script
                {
                    writeFile(file: nombre_archivo, text: stringRes)
                    println "Archivo generado"
                }
            }
        }
    }
    post
{
    always
    {
        echo "El pipeline se ha ejecutado. "
    }
    failure
    {
        echo 'EL pipeline fallo'
        script
        {
        def errorMessage = currentBuild.rawBuild.getLog(1000).join('\n')
        echo 'Detalles del error: ${errorMessage}'
        mail to: "soporte@dominio.com", subject: "Pipeline Fallo", body: "El pipeline no se ejecuto."
        }
    }
    unstable
    {
        echo "El pipeline no se ejecuto de forma estable."
    }
    success
    {
        echo "El pipeline se ejecutó correctamente"        
    }
}
}
