pipeline {
    agent any

    stages {
        stage('Install dependencies'){
            steps{
                sh 'npm install'
            }
        }

        stage('Run unit tests'){
            steps{
                sh 'npm run test'
            }
        }

        stage('Run build'){
            steps{
                sh 'npm run build'
            }
        }
    }
}