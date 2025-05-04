pipeline{
  agent:any

stages{
stage('checkout'){
steps{
  git 'https://github.com/your-user/your-repo.git'
}
}stage('Deploy to s3'){
steps{
withAws(region:'us-east-1', credentials:AKIAXZRLVBGIO4MZDAOH)
s3Upload(
bucket:'intern-project-nippa-abi-001',
                        includePathPattern: '**/*.html',
                        workingDir: '.'
)
}
}
}

}
