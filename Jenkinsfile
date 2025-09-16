pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/rsssharma224/web2-repo.git', branch: 'master'
            }
        }

        stage('Build') {
            steps {
                echo 'Simulating build...'
            }
        }

        stage('Test') {
            steps {
                echo 'Simulating tests...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to IIS site: MyAppNew'
                bat '''
                    powershell -NoProfile -ExecutionPolicy Bypass -Command "Import-Module WebAdministration; Remove-Item -Recurse -Force 'C:\\inetpub\\wwwroot\\MyAppNew\\*' -ErrorAction SilentlyContinue; Copy-Item -Path '.\\web\\*' -Destination 'C:\\inetpub\\wwwroot\\MyAppNew\\' -Recurse -Force; Restart-WebItem 'IIS:\\Sites\\MyAppNew'"
                '''
            }
        }
    }
}
