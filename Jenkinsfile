void getVarsSetup() {
    VERSION = sh(returnStdout: true, script: 'grep "version:" release.yml | cut -d" " -f2').trim()
}
pipeline {
    agent any
    stages {
        stage('Build and Release Feature') {
            when {
                branch 'feature*'
                beforeAgent true
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
        stage("Build and release - Tag") {
           when {
               tag '*'
               beforeAgent true
           }
        }
    }
}
