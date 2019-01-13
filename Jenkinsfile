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
    stage('Code Analysis') {
      parallel {
        stage('Code Analysis') {
          steps {
            withSonarQubeEnv('sonarquabe') {
              bat 'sonar-scanner'
            }

          }
        }
        stage('test reporint') {
          steps {
            bat 'gradle test'
          }
        }
      }
    }
    stage('Deployment') {
      steps {
        bat 'gradle uploadArchives '
      }
    }
    stage('Notify slack') {
      steps {
        slackSend(botUser: true, baseUrl: 'https://gradlecompany.slack.com/services/hooks/jenkins-ci/', channel: 'jenkins_notif', message: 'Integrtation terminer', token: 'p7Yfaycr0DCUIebHkeysa4QB')
      }
    }
  }
  tools {
    gradle 'Gradle_Latest'
  }
  environment {
    PATH = 'C:\\Program Files (x86)\\Java\\jdk1.8.0_131\\bin;C:\\Windows\\system32;D:\\sonarqube-7.3\\bin\\windows-x86-64;D:\\sonar-scanner-3.2.0.1227-windows\\bin'
  }
}