pipeline {
  agent any
  stages {
    stage('Docker Build') {
      steps {
        sh 'docker build -t feroracle/jenkins-docker:latest .'
      }
    }
    stage('Docker Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'dockerPassword', usernameVariable: 'dockerUser')]) {
          sh "docker login -u ${env.dockerUser} -p ${env.dockerPassword}"
          sh 'docker push feroracle/jenkins-docker:latest'
        }
      }
    }
  }
}