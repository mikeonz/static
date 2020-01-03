pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      steps {
     
    stage('Upload to AWS') {
      steps {
        sh  'echo "Hello World"'
        sh  '''
                    echo "Multiline shell steps works too"
                    ls -alh
            '''
        sh  'tidy -q -e *.html'
        withAWS(region:'us-west-2',credentials:'aws-static') {
                 sh 'echo "Uploading content with AWS creds"'
                     s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'pipeline-test-jenkins')
                 }
      }
    }

  }
}
