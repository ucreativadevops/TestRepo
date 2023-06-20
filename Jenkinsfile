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

        stage('Run SonarQube'){
            steps{
                withSonarQubeEnv('SonarQubeCursoCI') {
                    sh "/opt/sonar-scanner/bin/sonar-scanner -Dsonar.projectKey=AngularApp -Dsonar.sources=src"
                }
            }
        }

        stage('Run build'){
            steps{
                sh 'npm run build'
            }
        }
    }
}