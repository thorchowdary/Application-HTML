pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
               sh '/usr/local/bin/aws s3 ls'
            }
        }
        stage('Test') {
            steps {
            echo "hello"
            }
        }
        stage('Deploy') {
            steps {
                echo "deploy"
                sh 'aws s3 ls'
                echo $BUID_NUMBER
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline succeeded! Yay!'
        }
        failure {
            echo 'Pipeline failed. Sad face.'
        }
    }
}
