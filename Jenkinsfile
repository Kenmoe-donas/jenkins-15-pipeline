pipeline{
    agent any
    stages{
        stage("clone"){
            steps{
                sh 'echo "clone"'
                sh 'nproc'
            }
        }

        stage("test"){
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

