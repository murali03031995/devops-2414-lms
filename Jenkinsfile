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
    stage('Release LMS Frontend') {
        steps {
            script {
                echo "Releasing.."       
                def packageJSON = readJSON file: 'webapp/package.json'
                def packageJSONVersion = packageJSON.version
                echo "${packageJSONVersion}"  
                sh "zip -r lms-${packageJSONVersion}.zip webapp/dist/*"
                sh "curl -v -u admin:admin123 --upload-file lms-${packageJSONVersion}.zip http://44.203.125.161:8081/repository/lms/"     
        }
        }
    }
  }
}
