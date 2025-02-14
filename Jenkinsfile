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

    stage('Functional Test (API)') {
      steps {
        sh 'echo "Execute API/Functional Test cases"'
        git(url: 'https://github.com/daveharlowe/rbp-api-karate-test-automation', branch: 'main', credentialsId: 'JenkinsBlueOcean-Github')
        sh '''cd api-auto-fw/
mvn clean test'''
      }
    }

    stage('Functional Test (UI)') {
      steps {
        sh 'echo "Execute UI/Functional Test cases"'
      }
    }

    stage('Non Functional Test (API Perf)') {
      steps {
        sh 'echo "API performance testing)"'
        git(url: 'https://github.com/daveharlowe/rbp-api-jmeter-test-perf-testing', branch: 'main', credentialsId: 'JenkinsBlueOcean-Github')
        sh '''chmod 755 apache-jmeter-5.5/bin/jmeter;
apache-jmeter-5.5/bin/jmeter -n -t src/test/jmeter/rbp/scripts/GetRoom-all-rooms-rpb.jmx -l testresults.jtl
'''
      }
    }

    stage('Publish Test Reports') {
      steps {
        sh 'echo "Publish Test reports"'
      }
    }

  }
}