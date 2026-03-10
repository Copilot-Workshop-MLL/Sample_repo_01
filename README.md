# Employee Management System

A full-stack web application built with the MERN stack (MongoDB, Express.js, React.js, Node.js) for managing employee records, analytics, and HR operations.

## 🚀 Features

### ✅ Implemented (Backend)
- **Authentication & Authorization**
  - JWT-based authentication
  - Role-based access control (Admin, HR, User)
  - Secure password hashing with bcrypt
  - User profile management

- **Employee Management**
  - Complete CRUD operations
  - Advanced search and filtering
  - Pagination support
  - Bulk operations (delete, restore, update)
  - Soft delete with restore functionality
  - Data validation and error handling

- **Dashboard & Analytics**
  - Employee statistics and overview
  - Department-wise analytics
  - Salary analytics and reporting
  - Hiring trends analysis
  - Turnover analytics

- **API Features**
  - RESTful API design
  - Comprehensive error handling
  - Input validation and sanitization
  - Rate limiting and security headers

### 🔄 In Development (Frontend)
- React.js application with TypeScript
- Material-UI components
- Redux Toolkit for state management
- Responsive design for mobile and desktop
- Interactive charts and dashboards
- Form validation and user experience

## 🛠 Technology Stack

### Backend
- **Runtime**: Node.js 18+
- **Framework**: Express.js 4.18+
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: JWT + bcryptjs
- **Security**: Helmet, CORS, rate limiting
- **Validation**: express-validator
- **Logging**: Morgan

### Frontend
- **Framework**: React 18+ with TypeScript
- **UI Library**: Material-UI (MUI) v5
- **State Management**: Redux Toolkit + RTK Query
- **Routing**: React Router v6
- **Forms**: React Hook Form + Yup validation
- **Charts**: Chart.js with react-chartjs-2
- **HTTP Client**: Axios

### Database
- **Primary DB**: MongoDB 6.0+
- **ODM**: Mongoose
- **Caching**: Redis (optional)

### DevOps
- **Containerization**: Docker & Docker Compose
- **Environment**: dotenv configuration
- **Development**: Nodemon, Concurrently

## 📋 Prerequisites

- Node.js 18+ and npm
- MongoDB 6.0+ (local installation or Docker)
- Git

## 🚀 Quick Start

### Option 1: Automated Setup
```bash
# Clone the repository
git clone <repository-url>
cd employee-management-system

# Run the setup script
npm run setup

# Start development servers
npm run full:dev
```

### Option 2: Manual Setup

#### Backend Setup
```bash
# Install backend dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration

# Start MongoDB (if using local installation)
mongod

# Start the backend server
npm run dev
```

#### Frontend Setup
```bash
# Navigate to frontend directory
cd frontend

# Install frontend dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration

# Start the frontend development server
npm start
```

### Option 3: Docker Setup
```bash
# Build and start all services
npm run docker:up

# View logs
npm run docker:logs

# Stop services
npm run docker:down
```

## 🌐 Application URLs

- **Backend API**: http://localhost:3000
- **Frontend App**: http://localhost:3001 (Docker) or http://localhost:3000 (dev)
- **API Documentation**: http://localhost:3000/api/docs
- **Health Check**: http://localhost:3000/health

## 🔐 Default Credentials

```
Email: admin@company.com
Password: admin123
```

## 📚 API Documentation

### POST /auth/register
Register a new user account.

**Request Body:**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "securepassword123"
}
```

**Response (201):**
```json
{
  "success": true,
  "message": "User registered successfully",
  "user": {
    "id": 1234567890,
    "name": "John Doe",
    "email": "john@example.com",
    "createdAt": "2026-03-10T..."
  },
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

### POST /auth/login
Login with existing user credentials.

**Request Body:**
```json
{
  "email": "john@example.com",
  "password": "securepassword123"
}
```

**Response (200):**
```json
{
  "success": true,
  "message": "Login successful",
  "user": {
    "id": 1234567890,
    "name": "John Doe",
    "email": "john@example.com",
    "createdAt": "2026-03-10T..."
  },
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

### GET /auth/profile
Get current user profile (requires authentication).

**Headers:**
```
Authorization: Bearer <your-jwt-token>
```

**Response (200):**
```json
{
  "success": true,
  "user": {
    "id": 1234567890,
    "email": "john@example.com",
    "name": "John Doe"
  }
}
```

### GET /auth/users
Get all users (requires authentication).

**Headers:**
```
Authorization: Bearer <your-jwt-token>
```

**Response (200):**
```json
{
  "success": true,
  "users": [...],
  "count": 5
}
```

## Utility Endpoints

### GET /utils/date
Get current date in DD-MM-YYYY format.

### POST /utils/factorial
Calculate factorial of a number.

**Request Body:**
```json
{
  "number": 5,
  "method": "iterative"
}
```

## Testing the API

### Using cURL

**Register a user:**
```bash
curl -X POST http://localhost:3000/auth/register \
  -H "Content-Type: application/json" \
  -d '{"name":"Test User","email":"test@example.com","password":"password123"}'
```

**Login:**
```bash
curl -X POST http://localhost:3000/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","password":"password123"}'
```

**Access protected endpoint:**
```bash
curl -X GET http://localhost:3000/auth/profile \
  -H "Authorization: Bearer YOUR_JWT_TOKEN_HERE"
```

## Default Test User

For testing purposes, there's a default admin user:
- **Email:** admin@example.com
- **Password:** admin123

## Environment Variables

Make sure to set these in your `.env` file:
- `JWT_SECRET`: Secret key for JWT token signing
- `PORT`: Server port (default: 3000)
- `NODE_ENV`: Environment (development/production)

## Security Notes

- JWT tokens expire after 24 hours
- Passwords are hashed using bcrypt with salt rounds of 10
- This uses an in-memory store - replace with a database for production
- Change the JWT_SECRET in production
