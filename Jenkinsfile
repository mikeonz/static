pipeline {
  agent any
  stages {
    stage('Upload to AWS') {
      steps {
        sh  'echo "Hello World"'
        sh  '''
                    echo "Multiline shell steps works too"
                    ls -alh
            '''
        sh  'tidy -q -e *.html'
        withAWS(region:'us-west-2',credentials:'AKIAR3S3KTJ7YOV74E4N') {
                 sh 'echo "Uploading content with AWS creds"'
                     s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'pipeline-test-jenkins')
                 }
      }
    }

  }
}
