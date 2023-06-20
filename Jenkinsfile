pipeline {
    agent any

    stages {
        stage('Install Dependencies'){
            steps{
                sh 'npm install'
            }
        }

        stage('Syntax Verification'){
            steps{
                sh 'npm run lint'
            }
        }

        stage('Run Unit Tests'){
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

        stage('SonarQube Quality Gate') {
            steps {
                sleep 5
                timeout(time: 10, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
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