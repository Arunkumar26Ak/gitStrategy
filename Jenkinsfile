pipeline {
  agent any
  options {
    buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')
  }
  stages {
    stage('Hello') {
     steps {
        sh 'echo "TAG test 8.1.0"'
        // sh 'echo "Branch creating process starts here @@"'
        // sh 'git checkout -b 1.0_RC'
        // sh 'git push -u origin 1.0_RC'
        sh 'git tag -a tagName -m "Your tag comment"'
        sh 'git merge develop'
        sh 'git commit -am "Merged develop branch to master'
        sh "git push origin master"
     }
    }
  }
}
