pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch:'main', url:'https://github.com/NipunaGamage888/intern-static-website'  
            }
        }

        stage('Deploy to S3') {
            steps {
                withAWS(region: 'us-east-1', credentials: 'AKIAXZRLVBGIO4MZDAOH') {
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
