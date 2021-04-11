pipeline {
    agent {
        label 'build'
    }
    stages {
        stage('initialize') {
            steps {
                sh '''
                    npm ci
                '''
            }
        }
        stage('build') {
            steps {
                sh '''
                    npm run build
                '''
            }
        }
        stage('deploy') {
            steps {
                sh '''
                    aws s3 sync build s3://jcnix-ui-dev --delete --acl bucket-owner-full-control
                '''
            }
        }
    }
}