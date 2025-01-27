pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm  // Checks out the source code from your GitHub repo
            }
        }

        stage('S3 Upload') {
            steps {
                withAWS(region: 'us-east-1', credentials: '9b3b3615-bd33-456a-92a7-0f86526801e1') {
                    sh '''
                        # List contents to verify files are available
                        ls -la

                        # Upload the index.html file to the S3 bucket 
                        aws s3 cp index.html s3://jenkibucket/

                        # Optionally, you can upload additional assets (like CSS, JS, etc.)
                        aws s3 cp ./assets/ s3://jenbuckket / --recursive
                    '''
                }
            }
        }
    }
}
