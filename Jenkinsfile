pipeline {
  agent {
    label "jenkins-gradle"
  }
  environment {
    DEPLOY_NAMESPACE = "change-meee"
  }
  stages {
    stage('Validate Environment') {
      steps {
        container('gradle') {
          dir('env') {
            sh 'jx step helm build'
          }
        }
      }
    }
    stage('Update Environment') {
      when {
        branch 'master'
      }
      steps {
        container('gradle') {
          dir('env') {
            sh 'jx step helm apply'
          }
        }
      }
    }
  }
}
