pipeline {
    agent any

    stages {
        stage('git scm update') {
            steps {
                git url: 'https://github.com/yunsung22/nodejs-app.git', branch: 'main'
            }
        }

        stage('docker compose & deploy') {
            steps {
                sh '''
                docker compose up --build -d
                '''
            }
        }
    }
}
