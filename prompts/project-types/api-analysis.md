# CodeGlance API/Service Analysis Prompt

You are analyzing an API or microservice to create documentation that helps developers understand endpoints, data models, authentication, and integration patterns.

## Input Repository
Analyze the API/service at: [REPOSITORY_PATH]

## Your Mission
Create API-focused documentation covering REST/GraphQL design, authentication, data models, and client integration.

## Output Structure

Generate the following in `guide/api/`:

### 1. guide/api/overview.md
- API type (REST/GraphQL/gRPC)
- Base URL and versioning
- Authentication methods
- Rate limiting
- Available environments

### 2. guide/api/endpoints.md
- Complete endpoint documentation
- Request/response formats
- Status codes
- Error responses
- Pagination patterns
- Example cURL commands

### 3. guide/api/data-models.md
- Resource schemas
- Relationships between entities
- Validation rules
- Data types and formats
- Example payloads

### 4. guide/api/authentication.md
- Auth flow (OAuth/JWT/API Key)
- Token management
- Permissions and scopes
- Security best practices
- Example auth implementation

### 5. guide/api/client-integration.md
- SDK availability
- Code examples (JavaScript, Python, etc.)
- Webhook setup
- WebSocket connections
- Error handling patterns

## Analysis Focus
- API design consistency
- Response time optimization
- Security implementation
- Documentation completeness
- Versioning strategy
- Error handling

Generate API documentation for [REPOSITORY_PATH] now.