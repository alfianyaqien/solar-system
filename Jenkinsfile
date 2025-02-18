
pipeline {
  agent any
  tools {
    nodejs 'nodejs-23-8-0'
  }

  stages {
    stage('Installing Dependencies') {
      steps {
        sh 'npm install --no-audit'
      }
    }

    stage('NPM Dependency Audit ') {
      steps {
        sh '''
          npm audit --audit-level=critical
          echo $?
        '''
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
