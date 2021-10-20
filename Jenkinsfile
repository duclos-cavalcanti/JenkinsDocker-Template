pipeline {
    // Agent: where to execute, useful in jenkins clusters where you have different machines/agents to run a job
    agent any
        // {
        // docker { 
        //     image 'vivado:2018.3'            
        // }
    stages { // where the work happens, like makefile targets
        stage('Checkout') {
            steps { 
                // checkout scm
                echo "Checkout..."
            }
        }
        stage('Build') {
            steps {
                echo "Build..."
            }
        }

        stage('Test') {
            steps {
                echo "Test..."
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploy..."
            }
        }
    }
    post { 
        always {             
            cleanWs()
        }
    }
}
