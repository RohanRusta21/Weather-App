pipeline {
    agent any
    environment{
        image = "wededo4644/react_weather_app"
    }

    stages {
        stage('Github Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/RohanRusta21/Weather-App.git'
            }
        }
        stage('Building image') {
            steps{
                script {
                    docker.build("${image}")
                }
            }
        }
        stage('Pushing image') {
            steps{
                script {
                    withCredentials([string(credentialsId: 'dockerhubpass', variable: 'dockerhubpwd')]) {
                    sh 'docker login -u wededo4644 -p ${dockerhubpwd}'
                    sh 'docker push ${image}'
                    
                    }
                }
            }
        }
    }
}
