pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat(script: 'gradle build', returnStatus: true)
        bat 'gradle javadoc'
        archiveArtifacts 'build/libs/*,jar'
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
  environment {
    PATH = 'C:\\Program Files (x86)\\Java\\jdk1.8.0_131\\bin;C:\\Windows\\system32'
  }
}