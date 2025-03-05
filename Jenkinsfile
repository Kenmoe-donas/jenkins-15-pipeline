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
            }
        }
        stage("docker image tag"){
            steps{
                sh 'docker tag jenkins-cicd:latest 650959877739.dkr.ecr.us-east-1.amazonaws.com/jenkins-cicd:latest'
            }
        }
        stage("push image"){
            steps{
                sh 'docker push 650959877739.dkr.ecr.us-east-1.amazonaws.com/jenkins-cicd:$BUILD_ID'
            }
        }
    }
}

