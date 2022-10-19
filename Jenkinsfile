pipeline {
    agent any

    stages {
       stage('Source') {
            steps {
                echo "GIT PULL FROM REPO"
                cd dir
                ls *.xml | count
            }
        }
        stage('Build') {
            steps {
                echo 'BUILD NOW'
            }
        }
       stage('Test') {
            agent {
                docker { image 'sonar cube' }
            }
            steps {
                sh 'running test'
            }
        }
        
        stage('integrationTest') {
            agent {
                docker { image 'amazon/aws-cli' }
            }
            steps {
                sh 'aws chechk server'
                sh 'aws deploy {SERVER_IP}'
            }
        }
    }
}
