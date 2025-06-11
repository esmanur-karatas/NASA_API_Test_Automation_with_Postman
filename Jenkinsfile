pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run All Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Archive Report') {
            steps {
                publishHTML(target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: 'reports',
                    reportFiles: 'report.html',
                    reportName: 'Postman Test Report'
                ])
            }
        }
    }

    post {
        always {
            echo '✅ Pipeline tamamlandı. HTML raporunu rapor sekmesinde görebilirsin.'
        }
    }
}
