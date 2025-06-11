pipeline {
    agent any

    tools {
        nodejs 'NodeJS_22' // Eğer globalde NodeJS ayarlamadıysan bunu kaldırabilirsin.
    }

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
                // Eğer rapor reports/report.html şeklindeyse, bu kısım HTML raporu Jenkins'te göstermek için
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
            echo '✅ Pipeline completed. Check the HTML report in "reports/report.html".'
        }
    }
}
