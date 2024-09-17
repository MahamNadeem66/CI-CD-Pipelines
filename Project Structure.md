ci-pipeline/: Contains all the necessary pipeline, Docker, and Kubernetes files.
docs/: Documentation on the project workflow and technologies used.
images/: Screenshots and visuals of the pipeline.


## PHP

### 2. **Jenkinsfile** (Jenkins Pipeline Script)

```groovy
pipeline {
    agent any

    environment {
        REGISTRY = "dockerhubusername/webapp"
        DOCKER_CREDENTIALS_ID = 'docker-credentials'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/username/CI-CD-Pipeline-Bytewise.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${REGISTRY}:latest")
                }
            }
        }

        stage('Test Application') {
            steps {
                sh 'npm test'  // Assuming you have tests configured in your Node.js app
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('', DOCKER_CREDENTIALS_ID) {
                        dockerImage.push()
                    }
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f ci-pipeline/kubernetes/deployment.yaml'
                sh 'kubectl apply -f ci-pipeline/kubernetes/service.yaml'
            }
        }
    }

    post {
        always {
            echo 'CI/CD pipeline finished!'
        }
    }
}
