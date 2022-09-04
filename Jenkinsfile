pipeline {
  agent any
  options {
    buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')
  }
  stages {
    stage('Hello') {
      when{
        branch 'main'
      }
     steps {
        sh 'echo "TAG test 7.0"'
        sh 'echo "Branch creating process starts here @@"'
        sh 'git checkout -b 1.0_RC'
        sh 'git push -u origin 1.0_RC'
     }
    }
  }
}
