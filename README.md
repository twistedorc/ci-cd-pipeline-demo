CI/CD Pipeline Demo
This repository demonstrates a CI/CD pipeline using GitHub Actions to build, test, and deploy a simple application.
Setup Instructions
Prerequisites
Before setting up the CI/CD pipeline, ensure that the following tools are installed:
- Docker (https://www.docker.com/get-started)
- Python 3.8+ (https://www.python.org/downloads/)
- GitHub CLI (optional, for managing GitHub Actions locally)
Clone the Repository
Clone the repository to your local machine:
```bash
git clone https://github.com/your-username/ci-cd-pipeline-demo.git
cd ci-cd-pipeline-demo
```
Setting Up Virtual Environment
1. Create a virtual environment:
```bash
python3 -m venv venv
```

2. Activate the virtual environment:
  - On Linux `source venv/bin/activate`
  

3. Install dependencies:
```bash
pip install -r requirements.txt
```
Running Tests Locally
To run the tests locally, use the following command:
```bash
python -m unittest discover -s tests -p "*.py"
```
CI/CD Pipeline with GitHub Actions
The GitHub Actions CI/CD pipeline is defined in the `.github/workflows/ci-cd.yml` file. The pipeline will:
1. Build the application.
2. Run tests (only if the `SKIP_TESTS` secret is not set to `true`).
3. Build and push the Docker image to DockerHub.
GitHub Actions Workflow
The CI/CD pipeline is triggered on a `push` to the `main` branch.

### Workflow Breakdown:
- **Checkout code**: The first step checks out the repository code.
- **Set up Python**: The second step sets up Python 3.8.
- **Install dependencies**: The pipeline installs dependencies using `pip`.
- **Run tests**: If `SKIP_TESTS` secret is not set to `true`, it runs the tests.
- **Docker build and push**: Finally, the pipeline logs in to DockerHub, builds the Docker image, and pushes it to the DockerHub repository.
Secrets Required for GitHub Actions
To run the workflow, you need to set the following secrets in your GitHub repository:
- `DOCKER_USERNAME`: Your DockerHub username.
- `DOCKER_PASSWORD`: Your DockerHub password.
- `SKIP_TESTS`: Set this to `'true'` if you want to skip the tests during the pipeline execution (default is `'false'`).
Example Docker Commands
If you need to manually build and push the Docker image, you can use the following commands:
```bash
docker build -t <your-dockerhub-username>/flask-app:latest .
docker push <your-dockerhub-username>/flask-app:latest
```
Troubleshooting
Test Discovery Issues
If you encounter errors during the test discovery, ensure that:
- The `tests` directory contains an `__init__.py` file. This allows Python to recognize the directory as a package.
- Your test files follow the `*.py` pattern.

To run tests manually, use the command:
```bash
python -m unittest discover -s tests -p "*.py"
```
