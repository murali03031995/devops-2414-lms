pipeline {
agent {
node{
label 'slave'
}
} 
stages {
    stage('sonar analysis') {
        steps {
           sh 'cd api'
           sh 'docker run --rm -e SONAR_HOST_URL="http://44.203.125.161:9000" -e SONAR_SCANNER_OPTS="-Dsonar.projectKey=lms" -e SONAR_TOKEN="sqp_3c06cb664c70e76094ff651fd98d557e2f78fecb" -v ".:/usr/src" sonarsource/sonar-scanner-cli'
      }
    }
  }
}
