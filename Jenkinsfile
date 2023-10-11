pipeline {
    //agent any
    agent {
        label 'AGENT_1'
    } 
    stages {
        stage('Build') { 
            steps {
                echo "building"
                sh 'echo "This build stage form groovy script" > /tmp/build.txt'
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
