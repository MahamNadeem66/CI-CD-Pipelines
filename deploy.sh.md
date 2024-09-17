## deploy.sh
#!/bin/bash

echo "Deploying application to Kubernetes..."

# Apply Kubernetes configuration files
kubectl apply -f ci-pipeline/kubernetes/deployment.yaml
kubectl apply -f ci-pipeline/kubernetes/service.yaml

echo "Application deployed successfully!"

## Documentation Files
# Project Overview

This project automates the CI/CD process for a web application. By leveraging Jenkins, Docker, and Kubernetes, we ensure:
- Continuous Integration and testing of code.
- Automated containerization using Docker.
- Scalable deployments through Kubernetes.

This helps teams reduce manual effort, avoid human errors, and deliver reliable updates faster.
