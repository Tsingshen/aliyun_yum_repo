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
        sh 'ls && echo "abc" >/tmp/123.txst'
      }
    }
    stage('123.txt') {
      steps {
        archiveArtifacts(artifacts: '/tmp/123.txt', onlyIfSuccessful: true)
      }
    }
    stage('publish') {
      steps {
        readFile '**/123.txt'
      }
    }
  }
}