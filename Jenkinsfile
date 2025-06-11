pipeline {
    agent any

    environment {
        PATH = "/usr/local/bin:$PATH"
    }

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'npm install -g newman newman-reporter-htmlextra'
            }
        }

        stage('Run All Tests') {
            steps {
                script {
                    def exitCode = sh(
                        script: '''
                            newman run postman/collections/collection.json \
                            --reporters cli,htmlextra \
                            --reporter-htmlextra-export reports/report.html || true
                        ''',
                        returnStatus: true
                    )
                    echo "Newman exit code: ${exitCode}"
                    // Fail olsa da pipeline devam eder
                }
            }
        }

        stage('Archive Report') {
            steps {
                archiveArtifacts artifacts: 'reports/report.html', allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            echo "✅ Pipeline completed. Check the HTML report in 'reports/report.html'."
        }
    }
}
