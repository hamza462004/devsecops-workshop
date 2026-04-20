# DevSecOps Workshop App

A simple Node.js application built with Express for DevSecOps workshop demonstrations.

## Description

This project contains a basic web application that displays "DevSecOps Workshop Working!" when accessed. It's designed to demonstrate DevSecOps practices including containerization with Docker and deployment to Kubernetes.

## Features

- Simple Express.js web server
- Docker containerization
- Kubernetes deployment manifests
- Ready for CI/CD pipelines

## Prerequisites

- Node.js (version 18 or later)
- Docker
- Kubernetes cluster (for deployment)
- kubectl (for Kubernetes operations)

## Local Development

### Installation

1. Clone the repository:
   ```bash
   git clone <your-repo-url>
   cd devsecops-workshop-main
   ```

2. Install dependencies:
   ```bash
   cd app
   npm install
   ```

### Running Locally

Start the application:
```bash
npm start
```

The application will be available at `http://localhost:3000`

## Docker

### Building the Image

From the root directory:
```bash
docker build -t devsecops-app ./app
```

### Running with Docker

```bash
docker run -p 3000:3000 devsecops-app
```

## Kubernetes Deployment

### Prerequisites

- A running Kubernetes cluster
- kubectl configured to access your cluster
- GitHub Container Registry access (if using GHCR)

### Deploy to Kubernetes

1. Update the image reference in `k8s/deployment.yaml` with your actual image path:
   ```yaml
   image: ghcr.io/<your-username>/devsecops-app:latest
   ```

2. Apply the Kubernetes manifests:
   ```bash
   kubectl apply -f k8s/
   ```

3. Check the deployment:
   ```bash
   kubectl get pods
   kubectl get services
   ```

### Accessing the Application

The service is configured as NodePort. Find the assigned port:
```bash
kubectl get svc devsecops-svc
```

Access the application at `http://<node-ip>:<assigned-port>`

## Project Structure

```
.
├── app/
│   ├── Dockerfile          # Docker configuration
│   ├── index.js           # Main application file
│   └── package.json       # Node.js dependencies
└── k8s/
    ├── deployment.yaml    # Kubernetes deployment
    └── service.yaml       # Kubernetes service
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is for educational purposes in DevSecOps workshops.
