# ArtSpark API Documentation

This document provides comprehensive documentation for the RESTful API endpoints of the ArtSpark application. The API is built using Spring Boot and follows standard REST principles. It supports operations for user input processing, project idea generation, display, user profile management, and market analysis.

## Base URL
All endpoints are relative to the base URL: `http://localhost:8080/api` (for local development). In production, replace with the deployed domain (e.g., `https://artspark.example.com/api`).

## Authentication
- The API uses Spring Security for authentication.
- Basic authentication is required for protected endpoints (e.g., profile management). Use HTTP Basic Auth with username and password.
- Public endpoints (e.g., idea generation) may not require auth, but can be configured to do so.
- Tokens or JWT can be added in future iterations for enhanced security.
- Error response for unauthorized access: 401 Unauthorized.

## Request/Response Format
- **Request Body**: JSON (application/json)
- **Response Body**: JSON (application/json)
- **Error Responses**: Standard HTTP status codes with JSON body containing `error` and `message` fields.
- **Pagination**: For list endpoints, use query params `page` (default: 0) and `size` (default: 10). Responses include `content`, `totalElements`, `totalPages`.

## Endpoints

### 1. User Input and Project Idea Generation
Handles submission of user preferences and generation of AI-powered project ideas.

#### POST /generate-ideas
- **Description**: Submits user preferences to generate art project ideas using the AI model. Optionally incorporates market trends.
- **Request Parameters**:
  - Body: JSON object (UserPreferencesDTO)
    ```json
    {
      "artStyle": "string" (required, e.g., "Surrealism"),
      "theme": "string" (optional, e.g., "Dreamlike"),
      "medium": "string" (optional, e.g., "Digital"),
      "userType": "string" (optional, e.g., "artist" or "entrepreneur")
    }
    ```
- **Response**:
  - 200 OK: Array of ProjectIdea objects
    ```json
    [
      {
        "id": "string",
        "style": "string",
        "description": "string",
        "inspiration": "string",
        "trendScore": "string"
      }
    ]
    ```
  - 400 Bad Request: If validation fails (e.g., missing required fields)
    ```json
    {
      "error": "Bad Request",
      "message": "artStyle is required"
    }
    ```
- **Example**:
  - Curl: `curl -X POST -H "Content-Type: application/json" -d '{"artStyle": "Surrealism"}' http://localhost:8080/api/generate-ideas`

### 2. Project Idea Display
Retrieves generated project ideas.

#### GET /ideas
- **Description**: Fetches a paginated list of all project ideas (or filtered by query params).
- **Request Parameters**:
  - Query: `style` (optional, filter by art style), `page` (int, default 0), `size` (int, default 10)
- **Response**:
  - 200 OK: Paginated response
    ```json
    {
      "content": [
        {
          "id": "string",
          "style": "string",
          "description": "string",
          "inspiration": "string",
          "trendScore": "string"
        }
      ],
      "totalElements": 50,
      "totalPages": 5
    }
    ```
  - 404 Not Found: If no ideas match
- **Example**:
  - Curl: `curl -X GET http://localhost:8080/api/ideas?style=Surrealism&page=0&size=5`

#### GET /ideas/{id}
- **Description**: Retrieves details of a specific project idea by ID.
- **Request Parameters**:
  - Path: `id` (string, required)
- **Response**:
  - 200 OK: ProjectIdea object
    ```json
    {
      "id": "string",
      "style": "string",
      "description": "string",
      "inspiration": "string",
      "trendScore": "string"
    }
    ```
  - 404 Not Found: If ID does not exist
- **Example**:
  - Curl: `curl -X GET http://localhost:8080/api/ideas/12345`

### 3. User Profile Management
Manages user profiles, including saving favorites and retrieving preferences.

#### GET /profiles/{username}
- **Description**: Retrieves the user profile, including favorites and preferences.
- **Request Parameters**:
  - Path: `username` (string, required)
- **Response**:
  - 200 OK: UserProfile object
    ```json
    {
      "id": "string",
      "username": "string",
      "favorites": [
        {
          "id": "string",
          "style": "string",
          "description": "string"
        }
      ],
      "preferences": ["string", "string"]
    }
    ```
  - 404 Not Found: If user not found
- **Authentication**: Required
- **Example**:
  - Curl: `curl -X GET -u username:password http://localhost:8080/api/profiles/jack`

#### POST /profiles/favorite
- **Description**: Adds a project idea to the user's favorites.
- **Request Parameters**:
  - Query: `username` (string, required)
  - Body: JSON object (ProjectIdea)
    ```json
    {
      "id": "string",
      "style": "string",
      "description": "string"
    }
    ```
- **Response**:
  - 200 OK: Success message
    ```json
    {
      "message": "Favorite saved"
    }
    ```
  - 400 Bad Request: If invalid data
- **Authentication**: Required
- **Example**:
  - Curl: `curl -X POST -u username:password -H "Content-Type: application/json" -d '{"id": "12345", "style": "Surrealism"}' http://localhost:8080/api/profiles/favorite?username=jack`

### 4. Market Analysis
Provides insights into art trends and competition.

#### GET /market-analysis
- **Description**: Analyzes market trends for a specific art style or general overview.
- **Request Parameters**:
  - Query: `style` (string, optional; if omitted, returns general trends)
- **Response**:
  - 200 OK: Map of trends
    ```json
    {
      "Surrealism": 8.5,
      "Pixel Art": 7.2
    }
    ```
  - 400 Bad Request: If invalid query
- **Example**:
  - Curl: `curl -X GET http://localhost:8080/api/market-analysis?style=Surrealism`

## Error Handling
- All endpoints return standardized error responses:
  ```json
  {
    "error": "HTTP Status Code Description",
    "message": "Detailed error message",
    "timestamp": "ISO timestamp"
  }
  ```
- Common Codes: 400 (Bad Request), 401 (Unauthorized), 404 (Not Found), 500 (Internal Server Error)

## Rate Limiting
- Endpoints like `/generate-ideas` may have rate limits (e.g., 10 requests/minute per user) to prevent abuse. Configured via Spring Boot annotations.

## API Versioning
- Current version: v1 (included in base URL if needed, e.g., `/api/v1/`).
- Future changes will use versioning to avoid breaking changes.

## OpenAPI/Swagger
- Access interactive docs at `/swagger-ui.html` or `/v3/api-docs` (enabled via Springdoc dependency).
- Generate client code using the OpenAPI JSON.

This documentation is based on the project's technical specifications and code structure. Update as features evolve.
