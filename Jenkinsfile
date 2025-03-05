pipeline{
    agent any
    stages{
        stage("Code scan"){
            steps{
                sh 'trivy --version'
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

