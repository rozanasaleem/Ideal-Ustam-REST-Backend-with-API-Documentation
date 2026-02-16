## Error Handling

The Ideal Ustam API uses standard HTTP status codes to indicate success or failure of requests.

### Common Status Codes

- **200 OK**: The request was successful.
- **400 Bad Request**: The request payload or parameters were invalid.
- **401 Unauthorized**: Authentication failed or the JWT is missing/invalid.
- **404 Not Found**: The requested resource (e.g., car) does not exist.
- **500 Internal Server Error**: An unexpected error occurred on the server.

### Error Response Format

Error responses typically use a simple JSON structure with a `message` field:

```json
{
  "message": "Invalid request"
}
``+

Examples:

- **400 Bad Request**

```json
{
  "message": "Invalid request"
}
```

- **401 Unauthorized**

```json
{
  "message": "Unauthorized"
}
```

or:

```json
{
  "message": "Invalid or expired token"
}
```

- **404 Not Found**

```json
{
  "message": "Car not found"
}
```

### Validation & Domain Errors

- Authentication-related errors (e.g., wrong password, locked account) result in `401 Unauthorized` with an explanatory `message`.
- Domain errors such as trying to access or update a non-existent car result in `404 Not Found`.



