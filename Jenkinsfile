
pipeline {
  agent any
  stages {
    stage('Node NPM Version') {
      steps {
        sh 'node -v'
        sh 'npm -v'
      }
    }
  }
  tools {
    nodejs 'nodejs-23-8-0'
  }

}
