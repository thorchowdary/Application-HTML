pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
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
