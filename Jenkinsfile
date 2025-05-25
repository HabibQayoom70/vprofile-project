pipeline {
    agent any

    environment {
        CODE_REPO = 'https://github.com/hkhcoder/vprofile-project.git'
    }

    stages {
        stage('Clone Code Repository') {
            steps {
                echo "Cloning project code..."
                git url: "${env.CODE_REPO}", branch: 'main'
            }
        }

        stage('Download Dockerfile and docker-compose.yml') {
            steps {
                echo "Downloading Docker files..."
                sh """
                    
                   cd vprofile-project
                    wget https://raw.githubusercontent.com/HabibQayoom70/vprofile-project/main/Dockerfile
                    wget https://raw.githubusercontent.com/HabibQayoom70/vprofile-project/main/docker-compose.yml
                """
            }
        }

        stage('Run Docker Compose') {
            steps {
                echo "Running docker-compose up..."
                dir("vprofile-project") {
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
