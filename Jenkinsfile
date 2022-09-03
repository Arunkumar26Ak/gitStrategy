pipeline {
  agent any
  options {
    buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')
  }
  stages {
    stage('Hello') {
      steps {
        sh 'echo "Branch creating process starts here @@"'
        sh 'git checkout -b test'
        sh 'git push -u origin test'
      }
    }
  }
}
