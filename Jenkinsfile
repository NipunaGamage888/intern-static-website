pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-user/your-repo.git'  // Replace with your actual repo
            }
        }

        stage('Deploy to S3') {
            steps {
                withAWS(region: 'us-east-1', credentials: 'aws-creds') {
                    s3Upload(
                        bucket: 'intern-project-nippa-abi-001',
                        includePathPattern: '**/*.html',
                        workingDir: '.'
                    )
                }
            }
        }
    }
}
