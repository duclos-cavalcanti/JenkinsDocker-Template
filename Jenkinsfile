pipeline {
    agent any
        // { // where to execute
        // docker { 
        //     image 'vivado:2018.3'            
        // }
    }
    stages { // where the work happens
        stage('Checkout') {
            steps { 
                // checkout scm
                echo "Checkout"
            }
        }
        stage('Build') {
            steps {
                echo "Build"
            }
        }

        stage('Test') {
            steps {
                echo "Test"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploy"
            }
        }
    }
    post { 
        always {             
            cleanWs()
        }
    }
}
