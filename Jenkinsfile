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
                withAWS(region: 'us-east-1', credentials: '904a359d-f3e1-45b3-9c3f-5ec9ab0a7087') {
                    sh '''
                        # List contents to verify files are available
                        ls -la

                        # Upload the index.html file to the S3 bucket 
                        aws s3 cp index.html s3://jenkibucket/

                        # Optionally, you can upload additional assets (like CSS, JS, etc.)
                        aws s3 cp ./assets/ s3://jenkibucket/ --recursive
                    '''
                }
            }
        }
    }
}
