---
name: dotnet-architecture-analysis
description: Analyze .NET codebases (ASP.NET Core, worker services, class libraries, monoliths, modular monoliths, microservice solutions) with a senior-architect lens. Use when asked for architecture review, technical debt/risk assessment, layering and dependency analysis, security/observability/cloud readiness checks, or refactor and migration planning for C#/.NET projects.
---

# Dotnet Architecture Analysis

## Overview
Produce a structured architecture assessment for .NET repositories with concrete findings, file-level evidence, and a prioritized action plan.

## Workflow
1. Map solution topology first.
- Discover `.sln`, `.csproj`, startup files, and environment/config files.
- Build the project dependency graph from project references.

2. Identify architecture style and boundary quality.
- Determine style (layered, clean/onion, modular monolith, microservices, hybrid).
- Check whether dependency direction matches the intended style.

3. Evaluate by core architecture domains.
- Architecture and layering
- Data and persistence
- Integration/messaging
- Configuration/secrets
- Logging/observability
- Scalability/cloud readiness
- Security
- Technical debt and maintainability

4. Extract evidence-backed findings.
- Always attach file references for non-trivial claims.
- Prefer high-impact risks over cosmetic issues.

5. Deliver output in ordered sections.
- Keep concise but not shallow.
- End with a phased action plan.

## Required Evidence Checklist
For each review, verify at least these areas before finalizing:
- DI composition root and service lifetimes
- DbContext registration, tracking mode, transaction boundaries
- Repository/UoW behavior and `SaveChanges` ownership
- AuthN/AuthZ pipeline and sensitive endpoint coverage
- Secret handling in appsettings and environment
- Middleware order and exception handling
- Logging format and PII risk in logs
- Health checks, telemetry, tracing readiness
- Deployment/container orchestration artifacts
- Framework/runtime support status risk (target framework lifecycle)

## .NET-Specific Heuristics
- Flag direct `DbContext` usage from controllers as boundary erosion unless intentionally thin CRUD API.
- Flag `SaveChanges` in repositories when UoW pattern is present.
- Flag sync-over-async (`.Result`, `.Wait()`) in request paths.
- Flag static mutable request context usage (cross-request data leaks).
- Flag hardcoded connection strings, secrets, service credentials.
- Flag permissive CORS and insecure cookie/JWT settings.
- Flag missing resiliency for outbound calls (retry, timeout, circuit breaker).
- Flag over-logging request/response bodies without redaction policy.

## Output Contract
Return sections in this order:
1. General architecture analysis
2. Project structure analysis
3. Data layer
4. Messaging/integration
5. Configuration/environment
6. Logging/observability
7. Scalability/cloud readiness
8. Security
9. Technical debt and risks
10. Refactor recommendations and migration plan

For each section:
- `Current state`: short diagnosis
- `Risks`: prioritized bullets
- `Recommendations`: specific, implementable actions
- `Evidence`: file references

## Prioritization Model
Tag each recommendation with one of:
- `P0`: security, data loss, critical reliability
- `P1`: high operational risk or architectural drift
- `P2`: maintainability/performance improvements

Default roadmap format:
- Phase 1 (0-2 weeks): P0
- Phase 2 (2-6 weeks): P1
- Phase 3 (6-12 weeks): P2 and modernization

## References
- Use `references/review-checklist.md` for fast audit coverage.
- Use `references/refactor-patterns.md` to map findings to implementation patterns.
