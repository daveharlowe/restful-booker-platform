pipeline {
  agent none
  stages {
    stage('Build') {
      agent {
        label 'agent1'
      }
      steps {
        sh 'echo "Build Application from Trunk"'
      }
    }

    stage('Functional Test') {
      agent {
        label 'agent1'
      }
      steps {
        sh 'echo "Execute API/Functional Test cases"'
      }
    }

    stage('Non Functional Test (API Perf)') {
      agent {
        label 'agent1'
      }
      steps {
        sh 'echo "API performance testing)"'
      }
    }

    stage('Publish Test Reports via email') {
       agent {
        label 'agent1'
      }
      steps {
        sh 'echo "Publish Test reports via email"'
      }
    }

  }
}
