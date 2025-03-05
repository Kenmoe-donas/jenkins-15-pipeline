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

        stage("docker image build"){
            steps{
                sh 'docker -v'
            }
        }

        stage("push image"){
            steps{
                sh 'docker ps'
            }
        }
    }
}

