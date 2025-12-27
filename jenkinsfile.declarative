pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    } 
    stages {
        stage('Build') { 
            steps {
                echo "Building" 
            }
        }
        stage('Test') { 
            steps {
                echo "Testing" 
            }
        }
        stage('Deploy') { 
            steps {
                echo "Deploying"
            }
        }
    }
    post {
        always{
            echo 'I will Always say Hello Again'
            cleanWs()
        }
        success {
            echo 'I will Run if Success'

        }
        failure {
            echo 'I will Run if Failure'


        }
    }

}