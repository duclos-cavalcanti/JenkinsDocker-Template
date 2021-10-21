// Necessary plugins:
//      Credentials
//      Credentials Binding

// Jenkins Environment variables can be found in http://localhost:8080/env-vars.html/
// def EXAMPLE_VARIABLE = getGitChanges() // example user variable calling on groovy script

pipeline {
    // where to execute, useful in jenkins clusters where you have different machines/agents to run a job
    agent any
        // {
        // docker { 
        //     image 'vivado:2018.3'            
        // }

    // external configurations that can be provided to a build that changes some configuration
    // are very suitable for expressions
    parameters {
        // string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
        choice(name: 'VERSION', choices: ['1.1.0', '1.1.1'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }

    // provides build tools for our projects such as maven, gradle, yarn and jdk
    // check them in Manage Jenkins -> Global Tool Configuration -> Add Tool
    tools {
        maven 'Maven'
    }

    // example of user defined environmental variables
    environment {
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('global') 
        // function that can be used to import Jenkins credentials at build/runtime
        // to be able to use it, need to install "Credentials Binding" Plugin, probably 
        // already installed through Suggested plugins. Of course also needs the "Credentils" Plugin
    }

    // where the work happens, similar makefile targets
    stages {
        stage('Checkout') {
            steps { 
                // checkout scm
                echo "Checkout..."
            }
        }
        stage('Build') {
            steps {
                echo "Building version ${NEW_VERSION}"
                echo "Build..."
                // mvn do things
            }
        }

        stage('Test') {
            steps {
                when { // example of conditional
                    expression {
                        env.BRANCH_NAME == 'example_dev' && params.executeTests == true
                        // only builds the 'Test' job if branch
                    }
                }
                echo "Test..."
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploy..."
                echo "deploying with ${SERVER_CREDENTIALS}"
                echo "deploying with version ${params.VERSION}"
                // can also be done with wrappers like
                // withCredentials([
                //     usernamePassword(credentials: 'example_id', usernameVariable: USER, passwordVariable: PWD)
                // ])
                // sh "some script ${USER} ${PWD}"
            }
        }
    }

    // executes some logic after all stages are done
    post {
        always {  // always
            cleanWs()
        }
        success { // in case of success
            echo "Succeeded..."
        }
        failure { // in case of failure
            // example: email dev that last pushed a build
            echo "Failed..."
        }
    }
}
