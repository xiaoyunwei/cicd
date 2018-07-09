pipeline {
  agent any
  stages {
    stage('Build image') {
      steps {
        dir(path: 'Code\\CicdLab')
        bat 'docker build . -f CicdLab.WebApp\\Dockerfile -t cicdlabwebapp'
        catchError() {
          bat 'docker rm cicdlabwebapp_container --force'
        }

        bat 'docker run -p 8081:80 --name cicdlabwebapp_container cicdlabwebapp'
      }
    }
  }
}