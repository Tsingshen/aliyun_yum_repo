pipeline {
  agent {
    docker {
      image 'alpine'
      args '--tty=true'
    }

  }
  stages {
    stage('shell') {
      steps {
        sh 'ls && echo "abc" >/tmp/123.xml'
      }
    }
    stage('123.txt') {
      steps {
        archiveArtifacts(artifacts: '123.xml', onlyIfSuccessful: true)
      }
    }
    stage('publish') {
      steps {
        readFile '**/123.txt'
      }
    }
  }
}