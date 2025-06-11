pipeline {
    agent any

    environment {
        PATH = "${tool 'NodeJS_24'}/bin;${env.PATH}"  // Windows için noktalı virgül
    }

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

        stage('Prepare Reports Folder') {
            steps {
                bat 'if not exist reports mkdir reports'
            }
        }

        stage('Run Positive Tests') {
            steps {
                script {
                    def result = bat(returnStatus: true, script: 'newman run postman\\collections\\NASA_Positive_Tests.json -r cli,html --reporter-html-export reports\\positive_report.html')
                    if (result != 0) {
                        echo "⚠️ Positive Tests failed but pipeline will continue."
                    } else {
                        echo "✅ Positive Tests passed."
                    }
                }
            }
        }

        stage('Run Negative Tests') {
            steps {
                script {
                    def result = bat(returnStatus: true, script: 'newman run postman\\collections\\NASA_Negative_Tests.json -r cli,html --reporter-html-export reports\\negative_report.html')
                    if (result != 0) {
                        echo "⚠️ Negative Tests failed but pipeline will continue."
                    } else {
                        echo "✅ Negative Tests passed."
                    }
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'reports/*.html', fingerprint: true
            echo '✅ Pipeline tamamlandı. HTML raporlarını Jenkins içinde görebilirsin.'
        }
    }
}
