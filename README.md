# Job Founder Microservices Backend Project

## Table of Contents
- [Introduction](#introduction)
- [Architecture](#architecture)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Running the Application](#running-the-application)
- [Services](#services)
- [Deployment](#deployment)

## Introduction
The Job Founder Microservices Backend Project is a comprehensive backend application designed to manage job listings, user profiles, and job applications. The application is built using a microservices architecture, ensuring scalability, maintainability, and ease of deployment.

## Architecture
This project follows a microservices architecture, where each service is responsible for a specific functionality. The services communicate with each other using REST APIs. The architecture includes:
- **User Service**: Manages user information and authentication.
- **Job Listing Service**: Handles job postings and listings.
- **Application Service**: Manages job applications from users.
- **Blog Service**: Manages blog posts for users learning new technologies.
- **API Gateway**: Acts as a single entry point for all client requests, routing them to the appropriate service.
- **Configuration Service**: Manages configuration settings for all services.

## Technologies Used
- **JavaScript**: Primary programming language.
- **Node.js & Express.js**: Framework for building the microservices.
- **Docker**: Containerization of services.
- **Docker Compose**: Orchestration of multi-container Docker applications.
- **MongoDB**: Database for storing data.
- **Kafka**: Messaging queue for inter-service communication.
- **CI/CD:** GitHub Actions

## Installation
### Prerequisites
- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

### Clone the Repository
```bash
git clone https://github.com/Chanuth-silva10/job-founder-microservices-backend-project-app.git
cd job-founder-microservices-backend-project-app
```

## Build and Run with Docker
### Build the Docker images:
```bash
docker-compose build
```

### Start the services:
```bash
docker-compose up
```

## Running the Application
After setting up and starting the services, the application will be accessible at:

```bash
User Service:        http://localhost:4003
Job Listing Service: http://localhost:4002
Application Service: http://localhost:4001
Blog Service:        http://localhost:4004
API Gateway:         http://localhost:4000
```

## Services
#### User Service
Manages user registration, login, and profile management. It handles authentication and authorization for the entire application.

#### Job Listing Service
Handles the creation, update, and deletion of job listings. It allows users to browse and search for jobs.

#### Application Service
Manages the submission and tracking of job applications by users.

#### Blog Service
Allows users to post and read blog articles related to job search tips and new technologies.

#### API Gateway
Acts as a single entry point for all client requests, routing them to the appropriate microservice.

#### Proxy
Manages centralized configuration for all services, ensuring consistent and dynamic configuration management.
