## Endpoints

This document lists all public API endpoints exposed by the Ideal Ustam backend.

Base URL (local): `http://localhost:8080`

---

### Authentication & User Endpoints

#### Register User

- **Method**: `POST`
- **URL**: `/api/auth/signup`
- **Description**: Register a new user account.
- **Request body**:

```json
{
  "email": "user@example.com",
  "username": "carowner123",
  "password": "securePassword123"
}
```

- **Responses**:
  - `200 OK` – user created
  - `400 Bad Request` – validation or registration error

#### Login

- **Method**: `POST`
- **URL**: `/api/auth/login`
- **Description**: Authenticate user and return a JWT token.
- **Request body**:

```json
{
  "email": "user@example.com",
  "password": "securePassword123"
}
```

- **Responses**:
  - `200 OK` – returns token and user info
  - `401 Unauthorized` – invalid credentials

#### Request Password Reset

- **Method**: `POST`
- **URL**: `/api/auth/password-reset-request`
- **Description**: Initiates a password reset by sending an email with a reset token.
- **Request body**:

```json
{
  "email": "user@example.com"
}
```

- **Responses**:
  - `200 OK` – email sent

#### Confirm Password Reset

- **Method**: `POST`
- **URL**: `/api/auth/password-reset`
- **Description**: Resets the user password using the reset token.
- **Request body**:

```json
{
  "email": "user@example.com",
  "token": "reset-token-from-email",
  "newPassword": "newSecurePassword123"
}
```

- **Responses**:
  - `200 OK` – password reset successful

#### Get Authenticated User

- **Method**: `GET`
- **URL**: `/users/me`
- **Auth**: **Required** – `Authorization: Bearer <token>`
- **Description**: Returns the currently authenticated user.

- **Responses**:
  - `200 OK` – user object
  - `400 Bad Request` – if user details cannot be retrieved

#### List All Users

- **Method**: `GET`
- **URL**: `/users/`
- **Auth**: **Required** – `Authorization: Bearer <token>`
- **Description**: Returns a list of all users.

- **Responses**:
  - `200 OK` – list of users

---

### Car Endpoints

All car endpoints require authentication with a valid JWT:

```http
Authorization: Bearer <token>
```

#### Add User's Car

- **Method**: `POST`
- **URL**: `/api/cars/newcar`
- **Description**: Adds a new car associated with the authenticated user.
- **Request body**:

```json
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
```

- **Responses**:
  - `200 OK` – returns the created car with `id` and `userId`
  - `400 Bad Request` – invalid data
  - `401 Unauthorized` – missing or invalid token

#### Get User's Cars

- **Method**: `GET`
- **URL**: `/api/cars/user`
- **Auth**: **Required**
- **Description**: Returns all cars belonging to the authenticated user.

- **Responses**:
  - `200 OK` – list of car objects
  - `401 Unauthorized` – missing or invalid token

#### Get Car by ID

- **Method**: `GET`
- **URL**: `/api/cars/{id}`
- **Auth**: **Required**
- **Description**: Fetch a specific car by its `id`.

- **Path params**:
  - `id` (integer) – car identifier

- **Responses**:
  - `200 OK` – car object
  - `404 Not Found` – car not found

#### Update Car

- **Method**: `PUT`
- **URL**: `/api/cars/{id}`
- **Auth**: **Required**
- **Description**: Update an existing car.

- **Path params**:
  - `id` (integer) – car identifier

- **Request body**: same structure as **Add User's Car**.

- **Responses**:
  - `200 OK` – updated car object
  - `404 Not Found` – car not found

#### Delete Car

- **Method**: `DELETE`
- **URL**: `/api/cars/{id}`
- **Auth**: **Required**
- **Description**: Delete a car.

- **Path params**:
  - `id` (integer) – car identifier

- **Responses**:
  - `200 OK` – car deleted (empty body)
  - `404 Not Found` – car not found



