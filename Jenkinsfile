void getVarsSetup() {
    VERSION = sh(returnStdout: true, script: 'grep "version:" release.yml | cut -d" " -f2').trim()
}
pipeline {
  agent any
  options {
    buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')
  }
  stages {
    stage('Hello') {
     steps {
        sh 'echo ${VERSION}'
        sh 'echo "TAG test 8.1.0"'
     }
    }
    stage('Build and RC Tag Release - Develop') {
            when {
                branch 'develop'
                beforeAgent true
            }
            steps {
                  script {
                      getVarsSetup()
                      sh "git tag ${VERSION}-rc"
                      sh "git push origin ${VERSION}-rc"
                  }
            }
    }
    stage('Build and Tag Release - Master') {
            when {
                branch 'master'
                beforeAgent true
            }

            steps {
                script {
                    getVarsSetup()
                    sh "git tag ${VERSION}"
                    sh "git push origin ${VERSION}"
                }
            }
        }
  }
}
