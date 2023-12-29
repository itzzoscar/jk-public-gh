pipeline {
    agent any

    stages {
        stage('Cloning Git Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/itzzoscar/jk-public-gh.git'
            }
        }
        stage('Build Image') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        stage('Deploy Application') {
            steps {
                sh 'docker stop webapp_ctr'
                sh 'docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}'
            }
        }
    }
}
