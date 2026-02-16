# Ideal Ustam API Documentation

An AI-powered mechanic finder application that matches users with the most compatible mechanics based on their car's needs, mechanic proficiency, and Google reviews.

## Base URL
http://localhost:8080



### 1. Register User
POST http://localhost:8080/api/auth/signup

**Request:**
{
"email": "user@example.com",
"username": "carowner123",
"password": "securePassword123"
}


**Response (200 OK):**
{
"message": "User registered successfully",
"username": "carowner123"
}


### 2. Login
POST http://localhost:8080/api/auth/login

**Request:**
{
"email": "user@example.com",
"password": "securePassword123"
}

**Response (200 OK):**
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "username": "carowner123",
    "email": "user@example.com",
    "message": "Login successful"
}

### 3. Password Reset Request
POST http://localhost:8080/api/auth/password-reset-request

**Request:**
{
"email": "user@example.com"
}

**Response (200 OK):**
{
"message": "Password reset request sent successfully"
}

### 4. Password Reset
POST /api/auth/password-reset

**Request:**
{
    "email": "user@example.com",
    "token": "reset-token-from-email",
    "newPassword": "newSecurePassword123"
}

**Response (200 OK):**
{
"message": "Password reset successful"
}

Car Management Endpoints
All car endpoints require Authentication header:

Authorization: Bearer {your_jwt_token}


### 1. Add User's Car

POST http://localhost:8080/api/cars/newcar
{
    "brand": "BMW",
    "model": "3 Series",
    "year": 2019,
    "series": "320i",
    "kilometers": 65000.5,
    "transmission": "AUTOMATIC",
    "fuelType": "GASOLINE",
    "engineSize": "2.0L",
    "cylinders": "4",
    "horsepower": 184,
    "maxSpeed": 210,
    "torque": 290.0,
    "mileage": 28.5
}

**Response (200 OK):**
{
    "id": 1,
    "brand": "BMW",
    "model": "3 Series",
    "year": 2019,
    "series": "320i",
    "kilometers": 65000.5,
    "transmission": "AUTOMATIC",
    "fuelType": "GASOLINE",
    "engineSize": "2.0L",
    "cylinders": "4",
    "horsepower": 184,
    "maxSpeed": 210,
    "torque": 290.0,
    "mileage": 28.5,
    "userId": 1
}

### 2. Get User's Cars
GET http://localhost:8080/api/cars/user

**Response (200 OK):**
[
    {
        "id": 1,
        "brand": "BMW",
        "model": "3 Series",
        "year": 2019,
        "series": "320i",
        "kilometers": 65000.5,
        "transmission": "AUTOMATIC",
        "fuelType": "GASOLINE",
        "engineSize": "2.0L",
        "cylinders": "4",
        "horsepower": 184,
        "maxSpeed": 210,
        "torque": 290.0,
        "mileage": 28.5,
        "userId": 1
    }
    { "id": 2,
      "brand": "Mercedes",
        ...etc}
]


### 3. Get Car by ID

GET http://localhost:8080/api/cars/{id}

**Response (200 OK):**
{
    "id": 1,
    "brand": "BMW",
    ...etc
}

### 4. Update Car

PUT http://localhost:8080/api/cars/{id}

**Request:**
{
    "brand": "BMW",
    ...etc
}

**Response (200 OK):**
{
    "message": "Car updated successfully"
}

### 5. Delete Car

DELETE http://localhost:8080/api/cars/{id}

**Response (200 OK):**
{
    "message": "Car deleted successfully"
}

Error Responses

400 Bad Request:
{
    "message": "Invalid request"
}

401 Unauthorized:
{
    "message": "Unauthorized"
    "message": "Invalid or expired token"
}

404 Not Found:
{
    "message": "Car not found"
}

Data Enums 

Transmission Types
AUTOMATIC
MANUAL


Fuel Types
DIESEL
GASOLINE
ELECTRIC
HYBRID
