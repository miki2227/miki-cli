# Backend API Review Checklist

Use this checklist when reviewing backend PRs or designing new services.

## API Design
- [ ] Does the endpoint follow RESTful naming conventions (nouns, plural)?
- [ ] Are the correct HTTP status codes used (e.g., 201 for Created, 409 for Conflict)?
- [ ] Is there a standardized error response format?
- [ ] Is pagination implemented for list endpoints?
- [ ] Are query parameters validated for type and range?

## Database
- [ ] Are all joined columns indexed?
- [ ] Is there an N+1 query problem in the implementation?
- [ ] Are database transactions used where atomicity is required?
- [ ] Does the migration include a rollback script (if applicable)?
- [ ] Are sensitive fields (passwords, tokens) encrypted/hashed?

## Security
- [ ] Is the endpoint protected by appropriate AuthN/AuthZ?
- [ ] Is rate limiting applied to public or high-cost endpoints?
- [ ] Are secrets managed via environment variables/secret managers (never hardcoded)?

## Performance
- [ ] Is there caching for frequently accessed, slow-changing data?
- [ ] Are large response payloads compressed or truncated?
- [ ] Are expensive tasks offloaded to a background worker/queue?

## Observability
- [ ] Is the request context (Trace ID) passed through to all log statements?
- [ ] Are critical errors logged with sufficient metadata for debugging?
- [ ] Are key performance metrics being tracked (Latency, Error Rate)?
