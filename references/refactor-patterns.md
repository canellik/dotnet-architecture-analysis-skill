# Refactor Patterns

## Layering Repair
- Move controller business logic to application services.
- Replace direct infrastructure usage with interfaces in application layer.
- Keep composition root in API/host project.

## Repository and UoW Correction
- Make repositories persistence-ignorant regarding transaction finalization.
- Centralize `SaveChanges` in UoW/application service.
- Enforce one transaction boundary per use case.

## Integration Decoupling
- Replace internal self-HTTP calls with in-process service contracts.
- For cross-service integration, add retry + timeout + circuit breaker.
- Introduce domain events and outbox for reliable async integration.

## Security Hardening
- Move secrets out of source control.
- Enforce secure cookie/token settings by environment.
- Add policy-based authorization and endpoint audits.
- Add rate limiting and request validation guards.

## Observability Modernization
- Adopt structured logging schema.
- Add OpenTelemetry traces and metrics.
- Add health checks with dependency probes.
- Add log redaction/masking policies.

## Modularization
- Split by bounded context (identity, scheduling, integration, master data).
- Define explicit contracts between modules.
- Isolate migrations and integration tests per module where possible.
