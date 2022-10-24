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
                sh 'TESTING NOW'
            }
        }
        
        stage('integrationTest') {
            agent {
                docker { image 'maven:3.8.1-adoptopenjdk-11' }
            }
            steps {
                sh 'CHECKING SERVER'  
            }
        }
    }
}
