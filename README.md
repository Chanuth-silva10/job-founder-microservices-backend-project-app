# Job Founder Microservices Backend Project

## Table of Contents
- [Introduction](#introduction)
- [Architecture](#architecture)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Running the Application](#running-the-application)
- [Services](#services)
- [Configuration](#configuration)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [Contact](#contact)

## Introduction
The Job Founder Microservices Backend Project is a comprehensive backend application designed to manage job listings, user profiles, and job applications. The application is built using a microservices architecture, ensuring scalability, maintainability, and ease of deployment.

## Architecture
This project follows a microservices architecture, where each service is responsible for a specific functionality. The services communicate with each other using REST APIs. The architecture includes:
- **User Service**: Manages user information and authentication.
- **Job Listing Service**: Handles job postings and listings.
- **Application Service**: Manages job applications from users.
- **Blog Service**: Manages blog post for users learning new technologies.
- **API Gateway**: Acts as a single entry point for all client requests, routing them to the appropriate service.
- **Configuration Service**: Manages configuration settings for all services.

## Technologies Used
- **Java**: Primary programming language.
- **Spring Boot**: Framework for building the microservices.
- **Docker**: Containerization of services.
- **Docker Compose**: Orchestration of multi-container Docker applications.
- **MySQL**: Database for storing persistent data.
- **Kafka**: Messaging queue for inter-service communication.

## Installation
### Prerequisites
- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Java 11+](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)

### Clone the Repository
```bash
git clone https://github.com/Chanuth-silva10/job-founder-microservices-backend-project-app.git
cd job-founder-microservices-backend-project-app
