/*pipeline {
    agent any
    stages {
        stage('Do Stuff') {
            
            steps {
                echo "doing stuff"
                echo "more stuff"
            }
        }
    }
}*/
node {
 properties([[$class: 'ParametersDefinitionProperty', parameterDefinitions: [[$class: 'CascadeChoiceParameter', choiceType: 'PT_MULTI_SELECT', description: 'Select the Environment(s) to Deploy', name: 'DEPLOY_ENVIRONMENT', referencedParameters: 'BUILD_TYPE', filterable: false, filterLength: 1, script: [$class: 'GroovyScript', script: [sandbox: true, script: '''println "test"'''], fallbackScript: [sandbox: true, script: '''println "test"'''] ]]]]])
 echo 'Hello World'
}
