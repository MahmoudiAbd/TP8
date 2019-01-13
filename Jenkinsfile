pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat(script: 'gradle build', returnStatus: true)
        bat 'gradle javadoc'
        archiveArtifacts 'build/libs/*jar buil/doc/javadoc'
      }
    }
    stage('Mail Notification') {
      steps {
        mail(subject: 'jenkins', body: 'jenkins', from: 'pipeline', to: 'ea_mahmoudi@esi.dz')
      }
    }
  }
  tools {
    gradle 'Gradle_Latest'
  }
}