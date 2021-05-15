pipeline {
    agent any
    environment {
        GIT_TRACE=1
        GIT_TRACE_PERFORMANCE=1
        GIT_CURL_VERBOSE=1
        GIT_SSH_COMMAND="ssh -vvv"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Do Stuff') {
            steps {
                echo "doing stuff!"
                echo "more stuff"
                echo env.BRANCH_NAME
                echo env.CHANGE_ID
                sh 'notexist'
            }
        }
        stage('Parallel') {
            parallel {
                stage ('P1') {
                    steps {
                        echo "This is P1"
                    }
                    post {
                        always {
                            echo 'Post P1'
                        }
                    }
                }
                stage ('P2') {
                    steps {
                        echo "This is P2"
                    }
                    post {
                        always {
                            echo 'Post P2'
                        }
                    }
                }
            }
        }
        /*stage('Do More Stuff') {
            steps {
                echo "doing stuff"
                echo "more stuff"
            }
            post {
                always {
                    echo 'Post Do More Stuff'
                }
            }
        }*/
    }
    post {
        always {
            echo 'Post end of pipeline!'
        }
    }
}
/*node {
 properties([[$class: 'ParametersDefinitionProperty', parameterDefinitions: [[$class: 'CascadeChoiceParameter', choiceType: 'PT_MULTI_SELECT', description: 'Select the Environment(s) to Deploy', name: 'DEPLOY_ENVIRONMENT', referencedParameters: 'BUILD_TYPE', filterable: false, filterLength: 1, script: [$class: 'GroovyScript', script: [sandbox: true, script: '''println "test"'''], fallbackScript: [sandbox: true, script: '''println "test"'''] ]]]]])
 echo 'Hello Worldd'
}*/
