pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "Build Application from Trunk"'
      }
    }

    stage('Functional Test') {
      steps {
        sh 'echo "Execute API/Functional Test cases"'
      }
    }

    stage('Non Functional Test (API Perf)') {
      steps {
        sh 'echo "API performance testing)"'
      }
    }

    stage('Publish Test Reports via email') {
      steps {
        sh 'echo "Publish Test reports via email"'
      }
    }

  }
}
