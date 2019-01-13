pipeline {
  agent any
   tools {  gradle 'Gradle_Latest' }
  stages {
    stage('Build') {
      steps {
        bat(script: 'gradle build', returnStatus: true)
      }
    }
    stage('Mail Notification') {
      steps {
        mail(subject: 'jenkins', body: 'jenkins', from: 'pipeline', to: 'ea_mahmoudi@esi.dz')
      }
    }
  }
}
