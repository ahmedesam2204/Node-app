pipeline {
    agent any

    stages {
        stage('Prep') {
            steps {
                git branch: 'main', url: 'https://github.com/ahmedesam2204/Node-app.git'
            }
        }
        stage('CI') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'password', usernameVariable: 'username')]) {
                sh """
                   docker build . -f dockerfile -t ${username}/nodeapps:${BUILD_NUMBER}
                   docker login -u ${username} -p ${password}
                   docker push ${username}/nodeapps:${BUILD_NUMBER}
                   """
}
            }
        }
    }
}
