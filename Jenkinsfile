pipeline {
  agent { label 'vm102-Linux' }
  stages {
    stage('Start SoftwareUnderTest') {
      steps {
        sh '/usr/bin/docker-compose up -d'
        sh 'echo "Start Application in Dev env(Docker)"'
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
