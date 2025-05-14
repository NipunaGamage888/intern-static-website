pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Clone Repo') {
            steps {
                git credentialsId: 'githubintern',
                    url: 'https://github.com/NipunaGamage888/intern-static-website.git',
                    branch: 'main'
            }
        }

        stage('Deploy to EC2') {
            steps {
                sh '''
                    echo "Deploying..."
                    cp -r * /var/www/html/   # or wherever your web root is
                '''
            }
        }
    }
}
