pipeline {
  agent any
  stages {
    stage('Build image') {
      steps {
        bat 'docker build Code\\CicdLab -f Code\\CicdLab\\CicdLab.WebApp\\Dockerfile -t cicdlabwebapp'
      }
    }
    stage('Remove container') {
      steps {
        bat 'docker rm cicdlabwebapp_container --force'
      }
    }
    stage('Run container') {
      steps {
        bat 'docker run -p 8081:80 --name cicdlabwebapp_container cicdlabwebapp'
      }
    }
  }
}