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

        stage('Install Newman & Reporter') {
            steps {
                bat 'npm install -g newman newman-reporter-junitfull'
            }
        }

        stage('Run Positive Tests') {
            steps {
                script {
                    catchError(buildResult: 'UNSTABLE', stageResult: 'UNSTABLE') {
                        bat '''
                        if not exist reports mkdir reports
                        newman run postman/collections/NASA_Positive_Tests.json ^
                         -e postman/environments/NASA_ENV.postman_environment.json ^
                         -r cli,html,junitfull ^
                         --reporter-html-export reports/positive_report.html ^
                         --reporter-junitfull-export reports/positive_report.xml
                        '''
                    }
                }
            }
            post {
                always {
                    junit allowEmptyResults: true, testResults: 'reports/positive_report.xml'
                }
            }
        }

        stage('Run Negative Tests') {
            steps {
                script {
                    catchError(buildResult: 'UNSTABLE', stageResult: 'UNSTABLE') {
                        bat '''
                        if not exist reports mkdir reports
                        newman run postman/collections/NASA_Negative_Tests.json ^
                         -e postman/environments/NASA_ENV.postman_environment.json ^
                         -r cli,html,junitfull ^
                         --reporter-html-export reports/negative_report.html ^
                         --reporter-junitfull-export reports/negative_report.xml
                        '''
                    }
                }
            }
            post {
                always {
                    junit allowEmptyResults: true, testResults: 'reports/negative_report.xml'
                }
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
            echo '✅ Pipeline finished. Check Jenkins test results and HTML reports.'
        }
    }
}
