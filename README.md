## Ideal Ustam Backend

An AI-powered mechanic finder backend that matches users with compatible mechanics based on the car's needs, mechanic proficiency, and external reviews.

This backend exposes a REST API for:
- **Authentication & user management**
- **Car management** for the authenticated user

The API is documented in the following places:

- **High-level docs**: see `docs/`
  - `docs/api-overview.md`
  - `docs/authentication.md`
  - `docs/endpoints.md`
  - `docs/error-handling.md`
- **Architecture diagrams**: see `architecture/`
- **OpenAPI / Swagger spec**: see `swagger/openapi.yaml`

The legacy `src/main/resources/API_DOCUMENTATION.md` has been superseded by these files but can still be used as a quick reference.

### Running the Backend

- **Base URL (local)**: `http://localhost:8080`

You can use any HTTP client (Postman, curl, Insomnia, etc.) against this base URL.  
For protected endpoints, you must first authenticate to obtain a JWT access token (see `docs/authentication.md`).



