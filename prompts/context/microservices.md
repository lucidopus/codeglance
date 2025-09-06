# CodeGlance Microservices Analysis Prompt

You are analyzing a microservices architecture. Focus on service boundaries, communication patterns, and distributed system concerns.

## Input Repository
Analyze the microservices at: [REPOSITORY_PATH]

## Microservices-Specific Analysis

### Key Areas
- Service boundaries and responsibilities
- Inter-service communication
- Data consistency strategies
- Service discovery and routing
- Distributed tracing and monitoring

## Output Structure

Generate the following in `guide/microservices/`:

### 1. guide/microservices/overview.md
```markdown
# 🔗 Microservices Architecture

## Services Catalog
| Service | Purpose | Port | API Type | Database |
|---------|---------|------|----------|----------|
| [name] | [purpose] | [port] | [REST/gRPC] | [DB] |

## Communication Patterns
- Synchronous: [REST/gRPC/GraphQL]
- Asynchronous: [Message Queue/Event Bus]
- Service Mesh: [Yes/No - Details]
```

### 2. guide/microservices/service-map.md
Visual service dependencies:
```
    [API Gateway]
    /     |     \
[User]  [Order]  [Payment]
   |       |        |
[User DB] [Order DB] [Payment DB]
           |
    [Message Queue]
      /         \
[Email Service] [Analytics]
```

### 3. guide/microservices/api-contracts.md
For each service:
- Exposed endpoints
- Request/response formats
- Event schemas
- Error codes
- SLA requirements

### 4. guide/microservices/data-management.md
- Data ownership by service
- Cross-service data queries
- Transaction boundaries
- Eventual consistency handling
- Saga patterns (if used)

### 5. guide/microservices/communication.md
```markdown
## Synchronous Communication
- Service-to-service REST calls
- Circuit breaker configuration
- Retry policies
- Timeout settings

## Asynchronous Communication
- Message queue topics
- Event schemas
- Publisher/subscriber mappings
- Dead letter queues
```

### 6. guide/microservices/deployment.md
- Container orchestration (K8s/Docker)
- Service discovery mechanism
- Load balancing strategy
- Health checks
- Rolling deployment process

### 7. guide/microservices/observability.md
- Distributed tracing setup
- Centralized logging
- Metrics aggregation
- Service health dashboards
- Alert configurations

### 8. guide/microservices/development.md
- Local development setup
- Service mocking/stubbing
- Integration testing approach
- Debugging distributed requests
- Development tools

## Special Considerations
- Identify service coupling issues
- Document failure scenarios
- Note consistency boundaries
- Performance bottlenecks
- Security boundaries
- Service versioning strategy

Generate microservices analysis for [REPOSITORY_PATH] now.