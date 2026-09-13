# Vehicle Insurance Prediction - MLOps

A comprehensive end-to-end Machine Learning Operations (MLOps) project for predicting vehicle insurance outcomes. This project encompasses data ingestion from MongoDB, a full machine learning pipeline, model storage in AWS S3, and continuous integration/continuous deployment (CI/CD) to AWS EC2 using GitHub Actions and Docker.

## Key Features

*   **FastAPI Backend:** Provides RESTful APIs for both model prediction and triggering the training pipeline.
*   **Modular Architecture:** Designed with clear segregation for Data Ingestion, Validation, Transformation, Model Training, Evaluation, and Push components.
*   **MongoDB Integration:** Real-time data fetching and database operations using MongoDB Atlas.
*   **AWS Services:**
    *   **S3:** Model registry and artifact storage.
    *   **ECR:** Docker image registry.
    *   **EC2:** Application hosting using a self-hosted GitHub runner.
*   **CI/CD Pipeline:** Automated deployment workflow configured via GitHub Actions.
*   **Containerization:** Fully dockerized application for consistent environments.

## Tech Stack

*   **Programming Language:** Python 3.10
*   **Web Framework:** FastAPI, Uvicorn, Jinja2
*   **Database:** MongoDB Atlas
*   **Cloud Infrastructure:** AWS (S3, ECR, EC2, IAM)
*   **Containerization:** Docker
*   **CI/CD:** GitHub Actions
*   **Environment Management:** Conda

## Setup and Installation

### Prerequisites
*   Python 3.10
*   Conda
*   MongoDB Atlas Account
*   AWS Account with IAM credentials configured

### 1. Clone the Repository
```bash
git clone <repository-url>
cd MLOps-project-Vehicle-Insurance-Domain
```

### 2. Environment Setup
Create and activate a new Conda environment, then install dependencies:
```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt
```

### 3. Environment Variables Configuration
Set the following environment variables on your system:

**MongoDB URL:**
```bash
export MONGODB_URL="mongodb+srv://<username>:<password>@cluster.mongodb.net/..."
```

**AWS Credentials:**
```bash
export AWS_ACCESS_KEY_ID="your_access_key"
export AWS_SECRET_ACCESS_KEY="your_secret_key"
export AWS_DEFAULT_REGION="us-east-1"
```

## Usage

### Running Locally
Start the FastAPI application:
```bash
python app.py
```
By default, check your `src/constants` file for `APP_HOST` and `APP_PORT` to know where the application is running (commonly `http://0.0.0.0:5080` based on EC2 configuration).

### Endpoints
*   `GET /`: Renders the main vehicle data form.
*   `POST /`: Submits form data and returns the prediction result (Response-Yes / Response-No).
*   `GET /train`: Triggers the training pipeline manually.

## CI/CD Deployment

The CI/CD process is automated through GitHub Actions. Upon a push to the main branch:
1.  A new Docker image is built.
2.  The image is pushed to AWS ECR.
3.  The self-hosted runner on the AWS EC2 instance pulls the latest image and deploys the container.

## Author

**Raunak Sachdeva**