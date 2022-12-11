pipeline {
  agent {
    label 'vm102-Linux'
  }
  stages {
    stage('Start SoftwareUnderTest') {
      steps {
        sh 'echo "Start Application in Dev env(Docker)"'
        sh '/usr/bin/docker-compose up -d'
      }
    }

    stage('Functional Test') {
      steps {
        sh 'echo "Execute API/Functional Test cases"'
        git(url: 'https://github.com/daveharlowe/rbp-api-karate-test-automation', branch: 'main', credentialsId: 'Github-ssh-key')
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