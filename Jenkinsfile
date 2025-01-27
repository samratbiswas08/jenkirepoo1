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
                withAWS(region: 'us-east-1', credentials: '48f954b8-d55b-47e9-b791-227c2a5496cb') {
                    sh '''
                        # List contents to verify files are available
                        ls -la

                        # Upload the index.html file to the S3 bucket 
                        aws s3 cp index.html s3://jenkibucket/

                        # Optionally, you can upload additional assets (like CSS, JS, etc.)
                        aws s3 cp ./assets/ s3:// -jenbuckket -recursive
                    '''
                }
            }
        }
    }
}
