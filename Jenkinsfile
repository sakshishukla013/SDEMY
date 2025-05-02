pipeline {
    agent any

    environment {
        IMAGE_NAME = "sakshi644/sdemy-react-app"
    }

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/sakshishukla013/SDEMY.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Docker Build & Push') {
  steps {
    script {
      def app = docker.build("sakshishukla013/sdemy")
      docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials-id') {
        app.push("latest")
      }
    }
  }
}


        stage('Deploy') {
            steps {
                echo 'Deploying to production/staging...'
                // Add deployment steps here
            }
        }
    }
}
