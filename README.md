# SPE Mini Project – CI/CD Pipeline with Docker, Jenkins and Ansible

This mini project demonstrates a simple DevOps pipeline that automates the build, test, containerization, and deployment of a Python web application using Docker, Jenkins, and Ansible.

## Project Overview

The goal of this project is to implement a Continuous Integration and Continuous Deployment (CI/CD) workflow where code changes are automatically tested, containerized, and deployed. The project integrates multiple DevOps tools to simulate a real-world automated software delivery pipeline.

## Technologies Used

- Python
- Docker
- Jenkins
- Ansible
- HTML
- Git & GitHub

## Project Components

### Python Application
`main.py` contains the main backend logic for the web application.

### Static Web Page
The `static/index.html` file provides a simple frontend interface for the application.

### Docker
The `Dockerfile` is used to build a Docker image for the Python application so it can run consistently across different environments.

### Jenkins
The `Jenkinsfile` defines the CI/CD pipeline. Jenkins automates the following steps:
- Fetching the source code from GitHub
- Running automated tests
- Building the Docker image
- Deploying the application

### Ansible Deployment
Deployment is automated using Ansible.

Files used:
- `deploy.yml` – Ansible playbook for deployment
- `inventory` – List of target hosts

### Testing
`test.py` contains basic unit tests to verify the functionality of the Python application.

## CI/CD Workflow

1. Developer pushes code to GitHub
2. Jenkins detects the changes in the repository
3. Jenkins runs automated tests
4. Docker builds the application image
5. Ansible deploys the application to the target environment

## Project Structure

```
SPE-Mini/
│
├── main.py
├── test.py
├── Dockerfile
├── Jenkinsfile
├── deploy.yml
├── inventory
├── static/
│   └── index.html
├── SPE-Mini.pdf
└── README.md
```

## How to Run the Project

### Build Docker Image
```
docker build -t calculator-app .
```

### Run Docker Container
```
docker run -p 8000:8000 calculator-app
```

### Access the Application
Open your browser and visit:

```
http://localhost:8000
```

## Learning Outcomes

This project demonstrates:
- Containerization using Docker
- CI/CD automation using Jenkins
- Infrastructure automation using Ansible
- Integration of development and deployment workflows

## Author

Meenal Hirwani  
M.Tech – Computer Science
