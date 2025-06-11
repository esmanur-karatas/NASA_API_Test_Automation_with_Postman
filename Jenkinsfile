pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Install Newman') {
            steps {
                bat 'npm install -g newman'
            }
        }

        stage('Run All Tests') {
            steps {
                bat 'mkdir reports'
                bat 'newman run Postman_Collections/NASA.postman_collection.json -e Postman_Environments/NASA_ENV.postman_environment.json -r cli,html --reporter-html-export reports/report.html'
            }
        }

        stage('Archive Report') {
            steps {
                archiveArtifacts artifacts: 'reports/report.html', allowEmptyArchive: true
                publishHTML(target: [
                    reportDir: 'reports',
                    reportFiles: 'report.html',
                    reportName: 'NASA API Test Raporu'
                ])
            }
        }
    }

    post {
        always {
            echo '✅ Pipeline tamamlandı. HTML raporunu Jenkins içinde görebilirsin.'
        }
    }
}
