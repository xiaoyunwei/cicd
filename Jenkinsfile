pipeline {
  agent {
    dockerfile {
      filename 'Dockerfile'
    }

  }
  stages {
    stage('Run new container') {
      steps {
        bat 'docker build . -f CicdLab.WebApp/Dockerfile -t cicdlabwebapp'
        bat 'docker rm cicdlabwebapp_container --force'
        bat 'docker run -p 8081:80 -it --name cicdlabwebapp_container cicdlabwebapp'
      }
    }
  }
}