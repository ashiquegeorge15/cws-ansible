# Portfolio Website with Kubernetes Deployment

A modern, responsive portfolio website deployed using Docker and Kubernetes on WSL (Windows Subsystem for Linux).

## Project Overview

This project consists of a personal portfolio website with the following features:
- Responsive design for all device sizes
- Modern UI with smooth scrolling
- Sections for Home, About, Projects, and Contact
- Containerized deployment using Docker
- Kubernetes orchestration for high availability
- Nginx web server for serving static content

## Prerequisites

- Windows 10/11 with WSL2 enabled
- Docker Desktop with WSL2 backend
- Minikube
- kubectl
- Ansible (optional, for automation)

## Project Structure

```
portfolio-website/
├── src/
│   ├── index.html
│   ├── css/
│   │   └── styles.css
│   ├── js/
│   │   └── main.js
│   └── assets/
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
├── Dockerfile
└── README.md
```

## Local Development Setup

1. Clone the repository:
```bash
git clone <repository-url>
cd portfolio-website
```

2. Start local development server (optional):
```bash
# Using Python's built-in server
python -m http.server 8080
```

## Docker Build and Run

1. Build the Docker image:
```bash
docker build -t portfolio-website:latest .
```

2. Run the container locally:
```bash
docker run -d -p 8080:80 portfolio-website:latest
```

## Kubernetes Deployment

1. Start Minikube:
```bash
minikube start --driver=docker
```

2. Apply Kubernetes configurations:
```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

3. Verify deployment:
```bash
kubectl get pods
kubectl get services
```

4. Access the website:
```bash
minikube service portfolio-website
```

## Configuration

### Docker Configuration
The project uses `nginx:alpine` as the base image for minimal footprint. The Dockerfile copies static files to the appropriate nginx serving directory.

### Kubernetes Configuration
- Deployment configured with 2 replicas for high availability
- Resource limits set to prevent resource exhaustion
- Service type: LoadBalancer for external access

## Resource Specifications

### Deployment Resources
```yaml
resources:
  limits:
    cpu: "200m"
    memory: "256Mi"
  requests:
    cpu: "100m"
    memory: "128Mi"
```

## Troubleshooting

1. WSL File Permission Issues:
   - Ensure files are created in the correct WSL directory
   - Check file permissions with `ls -la`

2. Docker Build Issues:
   - Verify Dockerfile location
   - Ensure all referenced files exist
   - Check Docker daemon is running

3. Kubernetes Issues:
   - Verify minikube status
   - Check pod logs: `kubectl logs <pod-name>`
   - Describe resources: `kubectl describe pod/service`

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit changes
4. Push to the branch
5. Create a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

