pipeline {
    agent any

    stages {
        stage('Build and store in s3') {
            steps {
               zip -r package-$BUILD_NUMBER.zip *
               aws s3 cp package-$BUILD_NUMBER.zip s3://methorbucket
            }
        }

        stage('Deploy') {
            steps {
                ssh ec2-user@172.31.2.214
                cd /var/www/html
                aws s3 cp s3://methorbucket/package-$BUILD_NUMBER .
                echo "donwloading package from s3"
                unzip package-$BUILD_NUMBER.zip
                cp -r * /var/www/html
            }
        }
    }

    post {
        success {
            echo "success"
        }
        failure {
         echo "failure"
        }
    }
}
