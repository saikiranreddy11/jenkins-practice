// pipeline {
//     //agent any
//     agent {
//         label 'AGENT'
//     } 
//     stages {
//         stage('Build') { 
//             steps {
//                 echo "building"
//                 sh 'echo "This build stage form groovy script" > /tmp/build.txt'
//                 sh '''
//                 ls -l
//                 pwd
//                 echo "this is web hook example"
//                 '''
//             }
//         }
//         stage('Test') { 
//             steps {
//                 echo "testing"
//             }
//         }
//         stage('Deploy') { 
//             steps {
//                 echo "deploying"
//                  //error 'This stage failed because of an error condition.'
//             }
//         }
//     }
//     post { 
//         always { 
//             echo 'I will always say Hello again!'
//         }
//         success{
//             echo 'I will run when the job is success'
//         }
//         failure{
//             echo 'I will run when the job is failure'
//         }
// }


// }   

pipeline {
    agent{
        node{
            label 'AGENT'
        }
    }

    parameters {
        choice(
            name: 'TARGET_ENV',
            choices: 'development\nstaging\nproduction',
            description: 'Select the target environment for deployment'
        )
        booleanParam(
            name: 'DEPLOY',
            defaultValue: true,
            description: 'Deploy the application after build'
        )
    }

    stages {
        stage('Build') {
            steps {
                sh 'echo "Building the project"'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Running tests"'
            }
        }

        stage('Deploy') {
            when {
                expression {
                    return params.DEPLOY && currentBuild.resultIsBetterOrEqualTo('SUCCESS')
                }
            }
            steps {
                input {
                    message "Proceed with deployment to ${params.TARGET_ENV}?"
                    ok "Deploy"
                }
                sh "echo 'Deploying to ${params.TARGET_ENV}'"
            }
        }
    }

    post {
        success {
            echo "Build and test succeeded"
        }
        failure {
            echo "Build or test failed"
        }
        unstable {
            echo "Build is unstable"
        }
        always {
            echo "Pipeline completed"
        }
    }
}
