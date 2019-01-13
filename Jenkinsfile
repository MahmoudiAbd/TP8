pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'help'
      }
    }
    stage('Mail Notification') {
      steps {
        mail(subject: 'jenkins', body: 'jenkins', mimeType: 'text')
      }
    }
  }
}