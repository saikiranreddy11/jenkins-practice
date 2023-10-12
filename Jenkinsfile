pipeline {
    //agent any
    agent {
        label 'AGENT'
    } 
    stages {
        stage('Build') { 
            steps {
                echo "building"
                sh 'echo "This build stage form groovy script" > /tmp/build.txt'
                sh '''
                ls -l
                pwd
                echo "this is web hook example"
                '''
            }
        }
        stage('Test') { 
            steps {
                echo "testing"
            }
        }
        stage('Deploy') { 
            steps {
                echo "deploying"
                 //error 'This stage failed because of an error condition.'
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
        success{
            echo 'I will run when the job is success'
        }
        failure{
            echo 'I will run when the job is failure'
        }
}


}   
