# dotnet-architecture-analysis

Analyze .NET codebases with a senior-architect lens and produce structured, evidence-backed architecture reviews.

## What this skill does

This skill is designed for:

- ASP.NET Core applications
- Worker services
- Class libraries
- Monoliths / modular monoliths
- Microservice-based .NET solutions

It focuses on:

- architecture and layering quality
- technical debt and risk detection
- dependency and boundary analysis
- security and observability checks
- cloud readiness assessment
- refactor and migration planning

## Output format

The analysis is delivered in 10 sections:

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

Each section includes:

- Current state
- Risks
- Recommendations
- Evidence (file references)

## Prioritization model

- `P0`: security, data loss, critical reliability
- `P1`: high operational risk or architectural drift
- `P2`: maintainability/performance improvements

Default roadmap:

- Phase 1 (0-2 weeks): P0
- Phase 2 (2-6 weeks): P1
- Phase 3 (6-12 weeks): P2 and modernization

## Repository structure

- `SKILL.md`: core workflow and analysis contract
- `references/review-checklist.md`: audit checklist
- `references/refactor-patterns.md`: implementation-oriented refactor patterns
- `agents/openai.yaml`: UI metadata for the skill interface

## Usage

Use this skill when you need a structured architecture review of a C#/.NET repository with actionable, prioritized recommendations.

