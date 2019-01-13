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
        mail(subject: 'jenkins', body: 'jenkins', from: 'pipeline', to: 'ea_mahmoudi@esi.dz')
      }
    }
  }
}