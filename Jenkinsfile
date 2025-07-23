pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/kareliaru/Kampus_autotest.git', branch: 'develop'
            }
        }

        stage('Install Dependencies') {
            steps {
                powershell 'npm install --legacy-peer-deps --verbose'
            }
        }

        stage('Run API Tests') {
            steps {
                powershell 'npm run test'
            }
        }

        stage('Publish HTML Report') {
            steps {
                publishHTML([
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: 'reports',
                    reportFiles: 'newman-report.html',
                    reportName: 'Newman Test Report'
                ])
            }
        }
    }
}

