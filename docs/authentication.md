## Authentication

The Ideal Ustam API uses **JWT (JSON Web Token)** based authentication.

- Clients authenticate with `POST /api/auth/login` and receive a JWT.
- The JWT must be sent on subsequent requests in the `Authorization` header:

```http
Authorization: Bearer <token>
```

### Register a New User

- **Endpoint**: `POST /api/auth/signup`
- **Description**: Register a new user account.
- **Request body**:

```json
{
  "email": "user@example.com",
  "username": "carowner123",
  "password": "securePassword123"
}
```

- **Success (200)**: Returns the created user.

### Login

- **Endpoint**: `POST /api/auth/login`
- **Description**: Authenticate using email and password to obtain a JWT.
- **Request body**:

```json
{
  "email": "user@example.com",
  "password": "securePassword123"
}
```

- **Success (200)**:

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "username": "carowner123",
  "email": "user@example.com",
  "message": "Authentication successful"
}
```

- **Failure (401)**:

```json
{
  "message": "Authentication failed: <reason>"
}
```

### Password Reset Flow

The password reset flow has two steps: **request reset** and **confirm reset**.

#### 1. Request Password Reset

- **Endpoint**: `POST /api/auth/password-reset-request`
- **Description**: Initiates a password reset; sends a reset token to the user's email.
- **Request body**:

```json
{
  "email": "user@example.com"
}
```

- **Success (200)**:

```json
{
  "message": "Password reset email sent"
}
```

#### 2. Confirm Password Reset

- **Endpoint**: `POST /api/auth/password-reset`
- **Description**: Resets the user's password using the reset token.
- **Request body**:

```json
{
  "email": "user@example.com",
  "token": "reset-token-from-email",
  "newPassword": "newSecurePassword123"
}
```

- **Success (200)**:

```json
{
  "message": "Password successfully reset"
}
```



