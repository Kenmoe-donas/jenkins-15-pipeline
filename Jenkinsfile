pipeline{
    agent any
    stages{
        stage("clone web"){
            steps{
                sh 'echo "clone"'
                sh 'nproc'
            }
        }

        stage("test code"){
            steps{
                sh 'echo "test"'
            }
        }

        stage("create file"){
            steps{
                sh 'touch test-$BUIL_ID'
            }
        }
    }
}

