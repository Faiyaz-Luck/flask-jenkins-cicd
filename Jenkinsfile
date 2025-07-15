pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Faiyaz-Luck/flask-jenkins-cicd'
            }
        }

        stage('Build Image') {
            steps {
                sh 'podman build -t flaskapp .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                     podman stop flaskapp || true
                     podman rm flaskapp || true
                     podman run -d -p 5000:5000 --name flaskapp flaskapp
                '''
            }
        }
    }
}
