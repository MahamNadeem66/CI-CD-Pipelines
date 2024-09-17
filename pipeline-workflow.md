# Pipeline Workflow

1. **Clone Repository**: Jenkins pulls the latest code from GitHub.
2. **Build Docker Image**: The Dockerfile is used to create a Docker image for the web application.
3. **Test Application**: Jenkins runs automated tests to verify code quality.
4. **Push Docker Image**: The Docker image is pushed to Docker Hub.
5. **Deploy to Kubernetes**: The application is deployed to a Kubernetes cluster.

![Pipeline Workflow](../images/pipeline-screenshot.png)

## technologies-used

- **Jenkins**: For automating CI/CD tasks like building, testing, and deploying code.
- **Docker**: Used to create containerized environments for our web application.
- **Kubernetes**: Provides container orchestration, ensuring scalable and stable deployments.
- **GitHub**: Used as a version control platform for maintaining code integrity.
