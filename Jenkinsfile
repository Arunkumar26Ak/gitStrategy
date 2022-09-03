pipeline {
  agent any
  options {
    buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')
  }
  stages {
    stage('Hello') {
      steps {
        echo "Branch creating process starts here @@"
        git checkout -b 1_RC
        git add .
        git commit -a -m "I have added some changes"
        git push -u origin new-branch
      }
    }
  }
}
