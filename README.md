# 🚀 Job Founder Microservices Backend Project

## 🔍 Introduction

The **Job Founder Microservices Backend Project** is a comprehensive, production-ready backend application designed to manage job listings, user profiles, job applications, and educational blog content. Built with a modern microservices architecture, this system ensures high scalability, maintainability, and fault tolerance.

### ✨ Key Features
- **🔐 User Authentication & Authorization** - JWT-based secure authentication
- **💼 Job Management** - Complete CRUD operations for job listings
- **📝 Application Tracking** - End-to-end job application management
- **📖 Educational Blog Platform** - Tech blog management for career development
- **🖼️ File Upload Support** - Resume and image uploads via Cloudinary
- **🛡️ Role-Based Access Control** - Employer and Job Seeker roles
- **📊 RESTful APIs** - Well-structured API endpoints
- **🐳 Containerized Deployment** - Docker & Docker Compose ready

## 🏗️ Architecture

This project implements a **microservices architecture** with the following components:

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │   Nginx Proxy   │    │   Load Balancer │
│   (Port 5173)   │◄──►│   (Port 4000)   │◄──►│                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                               │
                    ┌──────────┼──────────┐
                    │          │          │
        ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
        │  User Service   │ │  Job Service    │ │ Application     │
        │  (Port 4002)    │ │  (Port 4001)    │ │ Service         │
        └─────────────────┘ └─────────────────┘ │--(Port 4003)----│
                    │          │          └─────────────────┘
        ┌─────────────────┐ ┌─────────────────┐
        │  Blog Service   │ │   MongoDB       │
        │  (Port 4004)    │ │   Database      │
        └─────────────────┘ └─────────────────┘
```

### 🔄 Service Communication
- **API Gateway Pattern**: Nginx reverse proxy routes requests to appropriate services
- **Database per Service**: Each service maintains its own data store
- **Stateless Services**: JWT tokens for maintaining user state
- **File Storage**: Cloudinary integration for media uploads

## 🛠️ Technologies Used

### **Backend Technologies**
- **Node.js** - JavaScript runtime environment
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database with Mongoose ODM
- **JWT** - JSON Web Tokens for authentication
- **bcryptjs** - Password hashing
- **Cloudinary** - Cloud-based image and video management

### **DevOps & Infrastructure**
- **Docker** - Application containerization
- **Docker Compose** - Multi-container orchestration
- **Nginx** - Reverse proxy and load balancer
- **GitHub Actions** - CI/CD pipeline

### **Development Tools**
- **Jest** - Testing framework
- **Nodemon** - Development auto-restart
- **CORS** - Cross-origin resource sharing
- **dotenv** - Environment variable management

## ⚡ Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/Chanuth-silva10/job-founder-microservices-backend-project-app.git
cd job-founder-microservices-backend-project-app
```

### 2. Environment Setup
Create `.env` files in each service directory or update the existing `config.env` files:

```bash
# Example configuration (update with your values)
PORT=4002
MONGO_URI=mongodb://localhost:27017/job-founder
JWT_SECRET_KEY=your-super-secret-jwt-key
JWT_EXPIRES=7d
COOKIE_EXPIRE=7
CLOUDINARY_CLIENT_NAME=your-cloudinary-name
CLOUDINARY_CLIENT_API=your-cloudinary-api-key
CLOUDINARY_CLIENT_SECRET=your-cloudinary-secret
FRONTEND_URL=http://localhost:5173
```

### 3. Run with Docker (Recommended)
```bash
# Build and start all services
docker-compose up --build

# Run in detached mode
docker-compose up -d --build
```

### 4. Manual Setup (Development)
```bash
# Install dependencies for each service
cd user && npm install && cd ..
cd job && npm install && cd ..
cd application && npm install && cd ..
cd blog && npm install && cd ..

# Start each service (in separate terminals)
cd user && npm start
cd job && npm start  
cd application && npm start
cd blog && npm start
```

## 🐳 Docker Setup

The application uses Docker Compose for orchestration. The setup includes:

### **Docker Compose Services**
- **user**: User management service (Port 4002)
- **job**: Job listing service (Port 4001)
- **application**: Job application service (Port 4003)
- **blog**: Blog management service (Port 4004)
- **nginx-proxy**: Reverse proxy (Port 4000)

### **Docker Commands**
```bash
# Build all services
docker-compose build

# Start services
docker-compose up

# View logs
docker-compose logs -f [service-name]

# Stop services
docker-compose down

# Remove volumes (careful - deletes data)
docker-compose down -v
```

## 🌐 API Endpoints

### **User Service** (`http://localhost:4000/user`)
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/register` | Register new user | ❌ |
| POST | `/login` | User login | ❌ |
| GET | `/logout` | User logout | ✅ |
| GET | `/getuser` | Get user profile | ✅ |

### **Job Service** (`http://localhost:4000/job`)
| Method | Endpoint | Description | Auth Required | Role |
|--------|----------|-------------|---------------|------|
| GET | `/getall` | Get all jobs | ❌ | All |
| POST | `/post` | Create new job | ✅ | Employer |
| GET | `/getmyjobs` | Get employer's jobs | ✅ | Employer |
| PUT | `/update/:id` | Update job | ✅ | Employer |
| DELETE | `/delete/:id` | Delete job | ✅ | Employer |
| GET | `/:id` | Get single job | ✅ | All |

### **Application Service** (`http://localhost:4000/application`)
| Method | Endpoint | Description | Auth Required | Role |
|--------|----------|-------------|---------------|------|
| POST | `/post` | Submit application | ✅ | Job Seeker |
| GET | `/employer/getall` | Get received applications | ✅ | Employer |
| GET | `/jobseeker/getall` | Get submitted applications | ✅ | Job Seeker |
| DELETE | `/delete/:id` | Delete application | ✅ | Job Seeker |

### **Blog Service** (`http://localhost:4000/blog`)
| Method | Endpoint | Description | Auth Required | Role |
|--------|----------|-------------|---------------|------|
| GET | `/getall` | Get all blogs | ❌ | All |
| POST | `/post` | Create blog post | ✅ | Employer |
| PUT | `/update/:id` | Update blog post | ✅ | Employer |
| DELETE | `/delete/:id` | Delete blog post | ✅ | Employer |
| GET | `/:id` | Get single blog | ✅ | All |

## 🔧 Services Overview

### **🔐 User Service**
- **Purpose**: Authentication, authorization, and user profile management
- **Features**: 
  - User registration with email validation
  - Secure password hashing with bcrypt
  - JWT token generation and validation
  - Role-based access (Employer/Job Seeker)
- **Database**: User profiles, credentials

### **💼 Job Service**
- **Purpose**: Job listing management
- **Features**:
  - CRUD operations for job postings
  - Job categorization and filtering
  - Salary range or fixed salary options
  - Job expiration handling
- **Database**: Job listings, categories, employer references

### **📝 Application Service**
- **Purpose**: Job application processing
- **Features**:
  - Resume upload via Cloudinary
  - Application submission and tracking
  - Employer-applicant matching
  - Application status management
- **Database**: Applications, resumes, applicant-employer relationships

### **📖 Blog Service**
- **Purpose**: Educational content management
- **Features**:
  - Tech blog creation and management
  - Content categorization
  - Author attribution
  - Rich text support
- **Database**: Blog posts, authors, categories

### **🌐 Nginx Proxy**
- **Purpose**: API Gateway and load balancing
- **Features**:
  - Request routing to appropriate services
  - CORS handling
  - Static file serving
  - SSL termination ready

## 🔐 Environment Configuration

### **Required Environment Variables**

Each service requires the following environment variables:

```env
# Server Configuration
PORT=4001                          # Service port number

# Database Configuration  
MONGO_URI=mongodb://localhost:27017/job-founder    # MongoDB connection string

# JWT Configuration
JWT_SECRET_KEY=your-super-secret-key               # JWT signing secret
JWT_EXPIRES=7d                                     # Token expiration time
COOKIE_EXPIRE=7                                    # Cookie expiration (days)

# Cloudinary Configuration (for file uploads)
CLOUDINARY_CLIENT_NAME=your-cloud-name            # Cloudinary cloud name
CLOUDINARY_CLIENT_API=your-api-key                # Cloudinary API key  
CLOUDINARY_CLIENT_SECRET=your-api-secret          # Cloudinary API secret

# Frontend Configuration
FRONTEND_URL=http://localhost:5173                # Frontend application URL
```

### **Port Configuration**
- **User Service**: 4002
- **Job Service**: 4001  
- **Application Service**: 4003
- **Blog Service**: 4004
- **Nginx Proxy**: 4000
- **Frontend**: 5173 (typical Vite/React setup)

## 🧪 Testing

### **Running Tests**
```bash
# Run tests for all services
docker-compose exec user npm test
docker-compose exec job npm test
docker-compose exec application npm test  
docker-compose exec blog npm test

# Run tests locally
cd user && npm test
cd job && npm test
cd application && npm test
cd blog && npm test
```

### **Test Coverage**
The project includes Jest test suites for:
- ✅ Controller functions
- ✅ Middleware validation
- ✅ Database operations
- ✅ API endpoint testing

## 📊 Project Structure

```
job-founder-microservices-backend-project-app/
├── 📁 user/                          # User Service
│   ├── 📁 controllers/               # Request handlers
│   ├── 📁 models/                    # Database schemas
│   ├── 📁 routes/                    # API routes
│   ├── 📁 middlewares/               # Custom middleware
│   ├── 📁 database/                  # DB connection
│   ├── 📁 utils/                     # Utility functions
│   ├── 📁 config/                    # Environment config
│   ├── 📄 app.js                     # Express app setup
│   ├── 📄 server.js                  # Server entry point
│   ├── 📄 package.json               # Dependencies
│   └── 📄 Dockerfile                 # Container config
│
├── 📁 job/                           # Job Service
│   └── [Similar structure to user/]
│
├── 📁 application/                   # Application Service  
│   └── [Similar structure to user/]
│
├── 📁 blog/                          # Blog Service
│   └── [Similar structure to user/]
│
├── 📁 proxy/                         # Nginx Proxy
│   ├── 📄 nginx.conf                 # Nginx configuration
│   └── 📄 Dockerfile                 # Nginx container
│
├── 📁 db/                            # MongoDB data (local)
├── 📄 docker-compose.yml             # Multi-container setup
└── 📄 README.md                      # Project documentation
```

---

<div align="center">
  <p>Built with ❤️ by <a href="https://github.com/Chanuth-silva10">Chanuth Silva</a></p>
  <p>⭐ Star this repo if you find it helpful!</p>
</div>
