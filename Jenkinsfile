pipeline {
    agent any
    
    tools {
        nodejs 'NodeJS' 
    }

    environment {
        FIREBASE_TOKEN = credentials('f45d4a52-418f-44be-a070-8b91ad64124f')
        
        TEST_ENV = 'arthur-test-626e4'
        STAGE_ENV = 'arthur-stage'
        PROD_ENV = 'arthur-prod-e5398'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Installing Firebase Tools...'
                sh 'npm install -g firebase-tools' 
            }
        }
        
        stage('Testing') {
            steps {
                echo 'Deploying to Testing environment...'
                sh "firebase deploy --only hosting --project ${TEST_ENV} --token ${FIREBASE_TOKEN}"
            }
        }
        
        stage('Staging') {
            steps {
                echo 'Deploying to Staging environment...'
                sh "firebase deploy --only hosting --project ${STAGE_ENV} --token ${FIREBASE_TOKEN}"
            }
        }
        
        stage('Production') {
            steps {
                echo 'Deploying to Production environment...'
                sh "firebase deploy --only hosting --project ${PROD_ENV} --token ${FIREBASE_TOKEN}"
            }
        }
    }
}