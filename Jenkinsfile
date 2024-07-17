pipeline {
    agent any
    
    parameters {
        string(name: 'PARAM1', defaultValue: '1', description: 'First parameter')
        string(name: 'PARAM2', defaultValue: '2', description: 'Second parameter')
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Check out the code from Git repository
                checkout scm
            }
        }
        stage('Create File') {
            steps {
                script {
                    def content = "Parameter 1: ${params.PARAM1}\nParameter 2: ${params.PARAM2}"
                    writeFile file: 'output.txt', text: content
                }
            }
        }
    }
    
    post {
        success {
            echo 'Parameters stored in output.txt successfully.'
        }
        failure {
            echo 'Failed to store parameters in output.txt.'
        }
    }
}
