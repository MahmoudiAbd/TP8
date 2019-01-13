pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './gradlew build'
      }
    }
    stage('Mail Notification') {
      steps {
        mail(subject: 'jenkins', body: 'jenkins', mimeType: 'text')
      }
    }
  }
}