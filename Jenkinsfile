pipeline{
    agent any
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
                sh 'aws ecr get-login-password --region us-east-1 | \
                docker login --username AWS --password-stdin 650959877739.dkr.ecr.us-east-1.amazonaws.com'
                
            }
        }
        stage("docker image build"){
            steps{
                sh 'docker build -t jenkins-cicd .'
                sh 'docker build -t jenkins-new .'
            }
        }
        stage("docker image tag"){
            steps{
                sh 'docker tag jenkins-cicd:latest 650959877739.dkr.ecr.us-east-1.amazonaws.com/jenkins-cicd:latest'
                sh 'docker tag jenkins-cicd:latest 650959877739.dkr.ecr.us-east-1.amazonaws.com/jenkins-new:v1.$BUILD_NUMBER'
            }
        }
        stage("push image"){
            steps{
                sh 'docker push 650959877739.dkr.ecr.us-east-1.amazonaws.com/jenkins-cicd:latest'
                sh 'docker push 650959877739.dkr.ecr.us-east-1.amazonaws.com/jenkins-cicd:v1.$BUILD_NUMBER'
            }
        }
    }
}

