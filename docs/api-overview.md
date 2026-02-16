## API Overview

This document provides a high-level overview of the Ideal Ustam REST API.

- **Base URL (local development)**: `http://localhost:8080`
- **Authentication**: JWT Bearer tokens (see `authentication.md`)
- **Content type**: JSON (`application/json`)

### Main Resource Groups

- **Authentication & Users**
  - `POST /api/auth/signup` – register a new user
  - `POST /api/auth/login` – authenticate and obtain a JWT token
  - `POST /api/auth/password-reset-request` – request a password reset email
  - `POST /api/auth/password-reset` – reset password using the emailed token
  - `GET /users/me` – retrieve the currently authenticated user
  - `GET /users/` – list all users

- **Cars**
  - `POST /api/cars/newcar` – add a new car for the authenticated user
  - `GET /api/cars/user` – list cars belonging to the authenticated user
  - `GET /api/cars/{id}` – fetch a specific car by ID
  - `PUT /api/cars/{id}` – update an existing car
  - `DELETE /api/cars/{id}` – delete a car

### Using the OpenAPI / Swagger Spec

For a machine-readable specification (for client generation, documentation UI, etc.), see:

- `swagger/openapi.yaml`

You can import this file into tools like Postman, Insomnia, or Swagger UI to explore and test the API.



