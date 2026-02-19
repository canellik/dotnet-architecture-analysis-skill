# Review Checklist

## Architecture and Boundaries
- Identify architecture style from project references and runtime composition.
- Check if API layer depends only on application contracts, not infrastructure internals.
- Check if domain layer is framework-independent.
- Verify module boundaries for high-churn features.

## Data and Transactions
- Confirm `DbContext` registration scope and tracking strategy.
- Confirm where `SaveChanges` is called.
- Confirm transaction orchestration location (application service preferred).
- Check index usage for frequent query paths.

## Integration and Messaging
- Detect synchronous coupling between internal modules/services.
- Check retry/timeouts for outbound HTTP.
- Check event publication reliability (outbox if needed).
- Check idempotency strategy for reprocessing endpoints/jobs.

## Configuration and Secrets
- Ensure no credential in repository.
- Confirm environment-specific settings are separated.
- Check if secure providers (Vault, KeyVault, Secrets Manager) are supported.

## Security
- Verify authentication scheme and token/cookie hardening.
- Verify endpoint-level authorization consistency.
- Check CORS, rate limit, and abuse protection.
- Check logging for sensitive field exposure.

## Observability and Operations
- Verify structured logging baseline.
- Verify health/readiness/liveness endpoints.
- Verify distributed tracing and correlation IDs.
- Verify operational runbooks for background jobs.

## Cloud Readiness
- Check statelessness assumptions.
- Check container/Kubernetes deployment readiness.
- Check externalized state and horizontal scaling blockers.
