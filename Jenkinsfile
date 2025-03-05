pipeline{
    agent any
    stages{
        stage("clone"){
            steps{
                sh 'echo "clone"'
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
