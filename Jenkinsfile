pipeline {
    agent any
    parameters{
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description:'')
    }
    // for accessing build tools
    tools{
       maven 'Maven'
    }
    environment{
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('jordy')
    }
    stages {
        stage('build') {
            steps {
                echo 'building'
                echo "building version ${NEW_VERSION}"
            }
        }
        stage('test') {
            // when{
            //     expression{
            //         BRANCH_NAME == 'dev' || BRANCH_NAME == 'master'
            //     }
            // }
            when{
                expression {
                    params.executeTests
                }
            }
            steps {
                echo "testing"
            }
        }
        stage('deploy') {
            steps {
                    echo "deployment"
                    echo "deploying version ${params.VERSION}"
            }
        }
    }
    post{
        always{
            //
        }
        success{
            //
        }
        failure{
            //
        }
    }
}
