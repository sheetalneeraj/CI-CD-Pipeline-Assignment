pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'ng build --prod'
            }
        }
        stage('Test') {
            steps {
                sh 'ng test --watch=false --browsers=ChromeHeadless'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
                // Simulate staging deployment with a simple copy command
                sh 'cp -R dist/sample-angular-app /var/www/staging'
            }
        }
        stage('Release to Production') {
            steps {
                input message: 'Ready to deploy to production?', ok: 'Deploy'
                echo 'Deploying to production...'
                sh 'cp -R dist/sample-angular-app /var/www/production'
            }
        }
    }
}
