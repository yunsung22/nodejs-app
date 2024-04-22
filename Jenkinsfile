pipeline {
    agent { label 'agent' }

    stages {
        stage('git scm update') {
            steps {
                git url: 'https://github.com/yunsung22/nodejs-app.git', branch: 'main'
            }
        }
        stage('docker build & deploy') {
            steps {
		sh 'IMAGE_NAME=yunsung22/nodejsapp docker compose build'
            }
        }
	stage('docker hub push') {
            steps {
                sh '''
 		   docker login -u yunsung22 -p dy455412!
                   docker push yunsung22/nodejsapp
		'''
            }
        }
	stage('microk8s run pod') {
            steps {
                sh ' microk8s kubectl run app1 --image=yunsung22/nodejsapp '
            }
        }
    }
}
