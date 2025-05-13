pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/NipunaGamage888/intern-static-website'
            }
        }

        stage('Deploy to EC2') {
            steps {
                sshagent (credentials: ['ec2_ssh']) {
                    sh '''
                        echo "Copying files to EC2 instance..."
                        scp -o StrictHostKeyChecking=no -r *.html ec2-user@<EC2_PUBLIC_IP>:/tmp/

                        echo "Moving files to web root..."
                        ssh -o StrictHostKeyChecking=no ec2-user@<EC2_PUBLIC_IP> '
                            sudo mv /tmp/*.html /var/www/html/
                        '
                    '''
                }
            }
        }
    }
}
