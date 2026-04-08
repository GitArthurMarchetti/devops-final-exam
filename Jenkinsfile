pipeline {
    agent any
    
    environment {
        FIREBASE_TOKEN = credentials('f45d4a52-418f-44be-a070-8b91ad64124f')
        
        TEST_ENV = 'arthur-test-626e4'
        STAGE_ENV = 'arthur-stage'
        PROD_ENV = 'arthur-prod-e5398'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Instalando Firebase Tools...'
                sh 'npm install -g firebase-tools' 
            }
        }
        
        stage('Testing') {
            steps {
                echo 'Fazendo deploy para o ambiente de Testing...'
                sh "firebase deploy --only hosting --project ${TEST_ENV} --token ${FIREBASE_TOKEN}"
            }
        }
        
        stage('Staging') {
            steps {
                echo 'Fazendo deploy para o ambiente de Staging...'
                sh "firebase deploy --only hosting --project ${STAGE_ENV} --token ${FIREBASE_TOKEN}"
            }
        }
        
        stage('Production') {
            steps {
                echo 'Fazendo deploy para o ambiente de Production...'
                sh "firebase deploy --only hosting --project ${PROD_ENV} --token ${FIREBASE_TOKEN}"
            }
        }
    }
}