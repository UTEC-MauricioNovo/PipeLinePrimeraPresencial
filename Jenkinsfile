pipeline {
  agent any
  stages {
    stage('Construyendo la App / Print Message') {
      steps {
        echo 'Paso 1 Construyendo la App'
        sh 'sh ejecutar_constructor_script.sh'
      }
    }

    stage('Ejecutando Linux') {
      steps {
        echo 'Realizando la prueba en Linux'
        sh 'sh ejecutar_test_linux.sh'
      }
    }

    stage('Comprobacion manual') {
      steps {
        echo 'Esperando la carroza'
        input 'ella hace ravioles, yo hago ravioles'
        timestamps() {
          echo 'Momento de confirmacion del agua caliente'
        }

      }
    }

    stage('Despliegue de Prod') {
      steps {
        echo 'Fin'
      }
    }

  }
  post {
    always {
      archiveArtifacts(artifacts: 'target/demoapp.jar', fingerprint: true)
    }

    failure {
      mail(to: 'mauricio.novo@estudiantes.utec.edu.uy', subject: "Failed Pipiline ${currentBuild.fullDisplayName}", body: "For details about the failure, see ${env.BUILD_URL}")
    }

  }
}