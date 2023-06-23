pipeline {
    agent any

    environment{
        AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_ID')
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
        AWS_DEFAULT_REGION = 'us-east-1'
    }

    stages {
        stage('Install Dependencies'){
            steps{
                sh 'npm install'
            }
        }

        stage('Run build'){
            steps{
                sh 'npm run build'
            }
        }

        stage('Deploy to AWS'){
            steps{
                sh 'aws s3 cp dist/clase6/ s3://demodeploymentclase10 --recursive'
            }
        }
    }
}
