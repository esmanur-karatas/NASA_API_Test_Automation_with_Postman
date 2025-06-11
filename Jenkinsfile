pipeline {
    agent any

    environment {
        PATH = "${tool 'NodeJS_24'}/bin:${env.PATH}"
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

        stage('Check Files') {
            steps {
                bat 'dir postman\\collections'
            }
        }

        stage('Run Positive Tests') {
            steps {
                bat 'if not exist reports mkdir reports'
                bat 'newman run postman/collections/NASA_Positive_Tests.json -r cli,html --reporter-html-export reports/positive_report.html'
            }
        }

        stage('Run Negative Tests') {
            steps {
                bat 'newman run postman/collections/NASA_Negative_Tests.json -r cli,html --reporter-html-export reports/negative_report.html'
            }
        }

        stage('Archive Reports') {
            steps {
                archiveArtifacts artifacts: 'reports/*.html', fingerprint: true
            }
        }
    }

    post {
        always {
            echo '✅ Pipeline tamamlandı. HTML raporlarını Jenkins içinde görebilirsin.'
        }
    }
}
