pipeline {
  agent {
    label 'vm102-Linux'
  }
  stages {
    stage('SelectReleaseVersionAndBuild SoftwareUnderTest') {
      steps {
        sh 'echo "Start Application in Dev env(Docker)"'
        sh '/usr/bin/docker-compose up -d'
      }
    }

    stage('Functional Test') {
      steps {
        sh 'echo "Execute API/Functional Test cases"'
        git(url: 'https://github.com/daveharlowe/rbp-api-karate-test-automation', branch: 'main', credentialsId: 'Github-ssh-key')
        sh '''cd api-auto-fw/
mvn clean test'''
      }
    }

    stage('Non Functional Test (API Perf)') {
      steps {
        sh 'echo "API performance testing)"'
        git(url: 'https://github.com/daveharlowe/rbp-api-jmeter-test-perf-testing', branch: 'main', credentialsId: 'Github-ssh-key')
      }
    }

    stage('Publish Test Reports') {
      steps {
        sh 'echo "Publish Test reports"'
      }
    }

  }
}