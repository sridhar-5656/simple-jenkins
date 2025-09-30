pipeline {
    agent any

    tools {
        nodejs "NodeJS_18"
    }

    environment {
        IMAGE_NAME = "jenkins-ci-cd-demo"
        DOCKER_HUB_USER = "your-dockerhub-username"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "📥 Checking out code..."
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "🛠️ Installing dependencies..."
                sh 'npm install --prefix app'
            }
        }

        stage('Test') {
            steps {
                echo "🧪 Running tests..."
                sh 'npm test --prefix app'
            }
        }

        stage('Docker Build') {
            steps {
                echo "🐳 Building Docker image..."
                sh "docker build -t $IMAGE_NAME ."
            }
        }

        stage('Docker Push') {
            steps {
                echo "📤 Pushing Docker image to DockerHub..."
                withCredentials([string(credentialsId: 'dockerhub-pass', variable: 'DOCKER_PASS')]) {
                    sh "echo $DOCKER_PASS | docker login -u $DOCKER_HUB_USER --password-stdin"
                    sh "docker tag $IMAGE_NAME $DOCKER_HUB_USER/$IMAGE_NAME:latest"
                    sh "docker push $DOCKER_HUB_USER/$IMAGE_NAME:latest"
                }
            }
        }

        stage('Deploy') {
            steps {
                echo "🚀 Deploying container..."
                sh "docker run -d -p 3000:3000 $DOCKER_HUB_USER/$IMAGE_NAME:latest"
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline executed successfully!"
        }
        failure {
            echo "❌ Pipeline failed. Check logs!"
        }
    }
}
