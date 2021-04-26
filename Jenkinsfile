pipeline {
  agent {
    label 'NODEJS'
  }

  stages {

    stage('Download Dependencies') {
      steps {
        sh '''
          npm install
        '''
      }
    }

    stage('Prepare Artifacts') {
      steps {
        sh '''
          zip -r user.zip node_modules server.js
        '''
      }
    }

    stage('Upload Artifacts') {
      steps {
        sh '''
          curl -f -v -u admin:admin123 --upload-file user.zip http://172.31.14.124:8081/repository/user/user.zip
        '''
      }
    }

  }

}