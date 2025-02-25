
pipeline {
  agent any
  tools {
    nodejs 'nodejs-23-8-0'
  }

  environment {
    MONGO_URI = "mongodb://127.0.0.1:27017/superData"
  }

  stages {
    stage('Installing Dependencies') {
      steps {
        sh 'npm install --no-audit'
      }
    }

    stage('NPM Dependency Audit') {
      steps {
        sh '''
          npm audit --audit-level=critical
          echo $?
        '''
      }
    }

    stage('Unit Testing') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'mongodb-credentials', passwordVariable: 'MONGO_PASSWORD', usernameVariable: 'MONGO_USERNAME')]) {
          sh 'npm test'
        }
      }
    }

    // stage('Dependency Scanning') {
    //   parallel {
    //     stage('NPM Dependency Audit ') {
    //       steps {
    //         sh '''
    //           npm audit --audit-level=critical
    //           echo $?
    //         '''
    //       }
    //     }
    //     stage('OWASP Scaning Dependencies') {
    //       steps {
    //         dependencyCheck additionalArguments: '''
    //           --scan \'./\'
    //           --out \'./\'
    //           --format \'ALL\'
    //           --prettyPrint''', odcInstallation: 'OWASP-DepCheck-10'
    //       }
    //     }
    //   }
    // }

  }

}
