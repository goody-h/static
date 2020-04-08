pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      steps {
        sh 'echo "Linting HTML files"'
        sh 'tidy -q -e *.html'
      }
    }
    stage('Upload to AWS') {
      steps {
        sh 'echo "Uploading site to s3 bucket"'
        withAWS(region:'us-east-2',credentials:'aws-static') {
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'udacity-jenkins-bucker')
        }
      }
    }
  }
}
