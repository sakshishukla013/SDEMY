pipeline {
    agent any

    environment {
        IMAGE_NAME = "sakshi644/sdemy-react-app"  // Recommended to use DockerHub-style naming
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/sakshishukla013/SDEMY'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Docker Build & Push') {
            steps {
                script {
                    def dockerImage = docker.build("${IMAGE_NAME}")
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials-id') {
                        dockerImage.push("latest")
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to production/staging...'
                
            }
        }
    }
}
