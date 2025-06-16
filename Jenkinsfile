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
                sh 'sudo podman build -t flaskapp .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                    sudo podman stop flaskapp || true
                    sudo podman rm flaskapp || true
                    sudo podman run -d -p 5000:5000 --name flaskapp flaskapp
                '''
            }
        }
    }
}
