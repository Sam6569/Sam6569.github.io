# CI/CD Demo

A simple Node.js Express application demonstrating automated CI/CD pipeline using GitHub Actions, Docker, and AWS EC2 deployment.

## Project Structure

```
ci-cd-demo/
├── .github/workflows/
│   └── ci-cd.yml          # GitHub Actions CI/CD pipeline
├── app.js                 # Express application
├── dockerfile             # Docker configuration
├── package.json           # Node.js dependencies and scripts
└── README.md             # Project documentation
```

## Application

Simple Express.js web server that:
- Serves "Hello from CI/CD demo!" on port 3000
- Demonstrates basic Node.js application structure

## CI/CD Pipeline

The GitHub Actions workflow (`.github/workflows/ci-cd.yml`) includes three stages:

### 1. Build and Test
- Checks out code
- Sets up Node.js 18
- Installs dependencies
- Runs tests

### 2. Docker Build and Deploy
- Builds Docker image
- Pushes to DockerHub registry
- Requires DockerHub credentials in secrets

### 3. Deploy to Staging
- Deploys to AWS EC2 instance
- Uses SSH for remote deployment
- Pulls latest Docker image and restarts container

## Setup

### Local Development
```bash
npm install
npm start
```

### Required GitHub Secrets
- `DOCKER_USERNAME` - DockerHub username
- `DOCKER_PASSWORD` - DockerHub password
- `SSH_PRIVATE_KEY` - SSH private key for EC2 access

## Deployment

The application automatically deploys to staging on pushes to the `main` branch. The deployment:
1. Pulls the latest Docker image
2. Stops and removes existing container
3. Runs new container on port 80

## Technologies

- **Runtime**: Node.js 18
- **Framework**: Express.js
- **Containerization**: Docker
- **CI/CD**: GitHub Actions
- **Deployment**: AWS EC2
- **Registry**: DockerHub