# Containerized Sports API Management System

This repository contains a **containerized sports API** designed for providing real-time sports data through a RESTful interface. The project leverages modern development tools such as **Docker**, **Python**, and other libraries to create an efficient, scalable, and reusable application.

## Features
- **Real-time Sports Data:** Fetch live data about games, teams, and scores.
- **Containerized Deployment:** Simplifies running the application using Docker.
- **Extensibility:** Easily adaptable for additional APIs or sports.
- **RESTful API:** Provides structured responses for easy integration.

## Technologies Used
- **Python**: Backend development using Flask.
- **Docker**: For containerized application deployment.
- **API Integration**: Sports data is retrieved via external APIs like the SERPAPI API.
- **Dependencies**:
  - `requests` for API calls.
  - `Flask` for REST API.
  - Additional libraries as defined in `requirements.txt`.

## Prerequisites
Before running the project, ensure you have the following installed:

- AWS Account
- Sport-API-Key from serpapi.com 
- Docker CLI and Desktop Installed.
- Install serpapi library in local environment 
- Python 3.8 or later.
- Git.

## Project Structure

```
sports-api-management/
├── app.py # Flask application for querying sports data
├── Dockerfile # Dockerfile to containerize the Flask app
├── requirements.txt # Python dependencies
├── .gitignore
└── README.md # Project documentation
```

## Installation and Setup

### **Clone the Repository**
   ```bash
   git clone https://github.com/ameh0429/containerized-sport-api.git
   cd containerized-sport-api
   ```

### **Set Up Environment Variables**
   Create a `.env` file in the root directory and populate it with the required API keys and configurations:
   ```env
   API_KEY=<Your_Sports_API_Key>
   ```

### **Create ECR Repo**
```bash
aws ecr create-repository --repository-name sports-api --region us-east-1
```

### **Build and push the Docker Image**
- Build the container using the provided `Dockerfile`:
```bash
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin <AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com

docker build --platform linux/amd64 -t sports-api .
docker tag sports-api:latest <AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/sports-api:sports-api-latest
docker push <AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/sports-api:sports-api-latest
```

### **Set Up ECS Cluster with Fargate**

- Create an ECS Cluster:
- Create a Task Definition:
- Run the Service with an ALB
- Test the ALB:
  
##### After deploying the ECS service, note the DNS name of the ALB (e.g., sports-api-alb-<AWS_ACCOUNT_ID>.us-east-1.elb.amazonaws.com)
Confirm the API is accessible by visiting the ALB DNS name in your browser and adding /sports 


### Configure API Gateway
- Create a New REST API:
- Set Up Integration:
- Deploy the API:

### Test the System
```bash
curl https://<api-gateway-id>.execute-api.us-east-1.amazonaws.com/prod/sports
```

## What We Learned
- **Containerization Benefits**: Leveraging Docker simplified application deployment and ensured consistency across development, testing, and production environments.
- **RESTful API Design**: Designing a scalable and maintainable REST API highlighted best practices, including versioning, error handling, and proper status code usage.
- **Cloud Deployment**: Deploying the application in the cloud provided insights into managing infrastructure, scaling resources, and ensuring system reliability.
- **Asynchronous Programming**: Utilizing asynchronous programming (e.g., with Python) improved API performance by handling multiple requests efficiently.

## Future Enhancements
- **Expand API Coverage**: Integrate additional sports leagues and events (e.g. MLB, FIFA) to make the API more comprehensive and cater to a wider audience.
- **Caching Mechanism**: Introduce a caching layer using tools like Redis or Memcached to improve API response times and reduce server load for frequently accessed data.
- **Enhanced Security**: Add authentication and authorization features using tools like OAuth2.0 or API key management for secure access to the API.
- **Mobile App Integration**: Build a companion mobile application to provide push notifications and an interactive interface for users to access real-time data on the go.


## Acknowledgments
- [NBA API](https://www.nba.com/stats) for live sports data.
- Docker and Python community for tools and libraries.
