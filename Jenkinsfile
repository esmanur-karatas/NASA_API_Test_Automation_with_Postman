pipeline {
    agent any

    tools {
        nodejs 'NodeJS_24'   // NodeJS aracını buradan çağırmak daha stabil
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

        stage('Run All Tests') {
            steps {
                bat 'if not exist reports mkdir reports'   // Hata vermez artık
                bat 'newman run Postman_Collections/NASA.postman_collection.json -e Postman_Environments/NASA_ENV.postman_environment.json -r cli,html --reporter-html-export reports/report.html'
            }
        }

        stage('Archive Report') {
            steps {
                archiveArtifacts artifacts: 'reports/report.html', fingerprint: true
            }
        }
    }

    post {
        always {
            echo '✅ Pipeline tamamlandı. HTML raporunu Jenkins içinde görebilirsin.'
        }
    }
}
