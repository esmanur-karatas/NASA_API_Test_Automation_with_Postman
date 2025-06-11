pipeline {
    agent any

    stages {
        stage('Install Newman') {
            steps {
                sh 'npm install -g newman'
            }
        }

        stage('Run Postman Tests') {
            steps {
                sh '''
                    newman run postman/collection.json \
                    --environment postman/environment.json \
                    --reporters cli
                '''
            }
        }
    }
}
