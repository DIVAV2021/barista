pipeline {
  agent any

  environment {
    IMAGE_NAME = 'divi2021/barista-site'
    CREDENTIALS_ID = 'docker-hub-credentials-id'
  }

  stages {
    stage('Build Docker Image') {
      steps {
        script {
          docker.build(IMAGE_NAME)
        }
      }
    }

    stage('Push Image to Docker Hub') {
      steps {
        script {
          docker.withRegistry('https://index.docker.io/v1/', CREDENTIALS_ID) {
            docker.image(IMAGE_NAME).push()
          }
        }
      }
    }
  }
}
