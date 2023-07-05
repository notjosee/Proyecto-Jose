pipeline{
    agent {
        label "linux-agent"
    }
  
    environment {
        LISTA_CORREOS = "josecursoci@gmail.com"
        CUERPO_CORREO = "El pipeline ${BUILD_URL} terminó su prueba de manera"
        TITULO_CORREO = "${BUILD_URL} Resultado"
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
                echo "Pruebas unitarias"
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
             emailext body: "${CUERPO_CORREO} exitosa", subject: "${TITULO_CORREO}", to: "${LISTA_CORREOS}"
        }
        failure {
            emailext body: "${CUERPO_CORREO} fallida", subject: "${TITULO_CORREO}", to: "${LISTA_CORREOS}"
        }
     }

    
}
