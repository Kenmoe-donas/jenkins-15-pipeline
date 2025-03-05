pipeline{
    agent any
    environment {
        cloud_region = "us-east-1"
        ecr_repo = '650959877739.dkr.ecr.us-east-1.amazonaws.com'
        imag_repo = '650959877739.dkr.ecr.us-east-1.amazonaws.com/jenkins-cicd'
    }
    stages{
        stage("Code scan"){
            steps{
                sh 'trivy --version'
                sh 'trivy fs . -o result.html'
                sh 'cat result.html'
            }
        }
        stage("docker login"){
            steps{
                sh "aws ecr get-login-password --region $cloud_region | \
                docker login --username AWS --password-stdin $ecr_repo"
                
            }
        }
        stage("docker image build"){
            steps{
                sh 'docker build -t jenkins-cicd .'
                
            }
        }
        stage("docker image tag"){
            steps{
                sh "docker tag jenkins-cicd:latest $imag_repo:latest"
                sh "docker tag jenkins-cicd:latest $image_repo:v1.$BUILD_NUMBER"
            }
        }
        stage("push image"){
            steps{
                sh "docker push $imag_repo:latest"
                sh "docker push $image_repo:v1.$BUILD_NUMBER"
            }
        }
    }
}