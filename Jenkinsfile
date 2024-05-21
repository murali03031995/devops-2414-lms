pipeline {
agent {
node{
label 'slave'
}
} 
stages {
    stage('build') {
        steps {
           sh 'cd webapp && npm install && npm run build'
      }
    }
    stage('nexus') {
        steps {
           sh 'zip -r lms-v1.1.zip webapp/dist/*'
           sh 'pwd'
           sh 'curl -v -u admin:admin123 --upload-file lms-v1.1.zip http://44.203.125.161:8081/repository/lms/'
      }
    }
  }
}
