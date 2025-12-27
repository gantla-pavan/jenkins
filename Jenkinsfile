pipeline {
    // tese are pre-build sections
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment {
        course = "Jenkins"
    } 
    options {
        timeout(time: 10, unit: 'MINUTES')
        disableConcurrentBuilds()

    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    // This is build section
    stages {
        stage('Build') { 
            steps {
                script{
                    sh """
                        echo "Building"
                        echo $COURSE
                        sleep 10
                        env
                        echo "Hello ${params.PERSON}"
                        echo "Biography: ${params.BIOGRAPHY}"
                        echo "Toggle: ${params.TOGGLE}"
                        echo "Choice: ${params.CHOICE}"
                        echo "Password: ${params.PASSWORD}"
                    """
                }
                
                
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
            
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
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