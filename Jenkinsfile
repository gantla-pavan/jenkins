pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment {
        course = "Jenkins"
    } 
    options {
        timeout(time: 10, unit: 'SECONDS') 
    }
    stages {
        stage('Build') { 
            steps {
                script{
                    sh """
                        echo "Building"
                        echo $COURSE
                        SLEEP 10
                        env
                    """
                }
                
                echo "Building" 
            }
        }
        stage('Test') { 
            steps {
                script{
                    sh """
                        echo "Testing"
                    """
                }
                echo "Testing" 
            }
        }
        stage('Deploy') { 
            steps {
                script{
                    sh """
                        echo "Deploying"
                    """
                }
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
        aborted {
            echo 'Pipeline is aborted'

        }
    }

}