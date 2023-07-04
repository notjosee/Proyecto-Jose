pipeline{
    agent {
        label "linux-agent"
    }

    stages{

        stage("Confirmación despliegue"){
            input{
                message "¿Desea comenzar el despliegue?"
                ok "Si"
            }
            steps{
              echo "Comenzando deploy"
            }
        }

        stage("Instalación de dependencias"){
            steps{
                sh "npm install"
            }
        }
        
        stage ("Prueba unitaria"){
            steps{
                echo "Comando de las pruebas unitarias npm run test"
            }
        }


        stage ("Compilación de la aplicación"){
            steps{
                sh "npm run build"
            }
        }

    }

    post{
        success {
            emailext body: "La prueba fue exitosa", subject: "Aviso", to: "josecursoci@gmail.com"
        }
        failure {
            emailext body: "La prueba tuvo un fallo", subject: "Aviso", to: "josecursoci@gmail.com"
        }
     }

    
}
