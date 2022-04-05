pipeline{
    agent any
     stages {
        stage('Git Checkout') {
          steps {
            echo "step1"
            checkout scm
          }
        }
        stage('Building Docker Image'){
            steps{
                echo 'step2'
                sh 'docker --version'
            }
        }
        stage('Deploy'){
            steps{
		sh "eval \$(aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/c76l3ps9)"
                sh "docker build . -t venkata-assignment"
                sh "docker push public.ecr.aws/c76l3ps9/venkata-assignment:latest"
            }
        }
     }
}
