CI/CD Pipeline Demo
This repository demonstrates a CI/CD pipeline using GitHub Actions to build, test, and deploy a Python application.

Prerequisites
Before setting up, ensure the following tools are installed:

Docker: Get Started
Python 3.8+: Download
(Optional) GitHub CLI: For managing Actions locally

Setup
Clone the repo:
git clone https://github.com/your-username/ci-cd-pipeline-demo.git  
cd ci-cd-pipeline-demo  

Set up a virtual environment:
python3 -m venv venv  
source venv/bin/activate  # For Linux  
pip install -r requirements.txt  

Running Tests Locally
Run tests with:
python -m unittest discover -s tests -p "*.py"  

GitHub Actions Workflow
The CI/CD pipeline is defined in .github/workflows/ci-cd.yml and triggers on pushes to the main branch. Key steps:

Checkout Code: Pulls the latest repo code.
Setup Python: Configures Python 3.8.
Install Dependencies: Installs required packages.
Run Tests: Executes tests unless SKIP_TESTS is set to true.
Docker Build & Push: Builds and pushes the Docker image to DockerHub.
Required Secrets
Set these secrets in your GitHub repo:

DOCKER_USERNAME: DockerHub username
DOCKER_PASSWORD: DockerHub password
SKIP_TESTS: Optional, set to true to skip tests
Docker Commands
To build and push manually:
docker build -t <username>/flask-app:latest .  
docker push <username>/flask-app:latest  

Troubleshooting
Ensure tests/ contains __init__.py for Python to recognize it as a package.
Test files should match the *.py pattern.
