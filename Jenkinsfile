pipeline {
    agent any
    environment {
      VERSION = 1
      BUILD_DATE = sh(returnStdout: true, script: 'echo $(date "+%Y%m%d-%H%M%S")').trim()
    }
    parameters {
    gitParameter branchFilter: 'origin/(.*)',
                 name: 'BRANCH',
	 	 quickFilterEnabled: 'true',
                 type: 'PT_BRANCH'
    }
    stages {
        stage('Do Stuff') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: "dockerfile"]],
                    doGenerateSubmoduleConfigurations: false,
                    extensions: [],
                    submoduleCfg: [],
                    userRemoteConfigs: [[url: 'https://github.com/dyland-test/first-repo.git',credentialsId: '85262083-3829-4e50-a8fb-853e55bd3236']]
                    ])
                echo "doing stuff"
                echo "more stuff"
                echo env.BRANCH_NAME
                echo env.CHANGE_ID
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
