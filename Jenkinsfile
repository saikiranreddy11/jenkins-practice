pipeline {
    //agent any
    agent {
        label 'AGENT_1'
    } 
    stages {
        stage('Build') { 
            steps {
                echo "building"
                echo "This build stage form groovy script" > /tmp/build.txt
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
}