# Project Context Generator — Claude Code Skill

A Claude Code skill that transforms any project idea into a fully structured AI development context repository — ready to use as a knowledge base for your entire dev team.

## What It Does

When you share a project idea, this skill breaks it down and generates a complete `docs/` folder with:

| Section | Contents |
|---------|----------|
| Product Vision | Vision statement, phased roadmap, design principles, success criteria |
| Domain Knowledge | Glossary, user personas, business objectives, functional requirements |
| Architecture | C4 system diagram, tech stack, ADRs, scalability strategy, caching, DB scaling |
| Security | Auth (JWT/RBAC/ABAC), OWASP Top 10 controls, PII handling, security checklist |
| Module Specs | Data models with indexes, workflows, scalability considerations per module |
| User Stories | US-001 format with acceptance criteria, business rules, dependencies |
| Workflows | End-to-end operational flows, per-role user flows, exception scenarios |
| Error Handling | RFC 7807 error shape, structured log format, retry/circuit-breaker policy |
| Deployment | 4-environment strategy, CI/CD pipeline, infrastructure overview, rollback runbook |
| Testing | Unit/integration/E2E strategy + load testing targets |
| API Contracts | OpenAPI 3.0 specs with pagination and rate-limit headers |

## Install

```bash
claude plugin install github:Amsiam/Project-Context-Generator-Skill
```

## Usage

Start a new Claude Code session and share your idea:

> "I want to build a hospital appointment booking system"

The skill triggers automatically and will:
1. Ask 8 clarifying questions (one at a time) — including expected scale, user roles, and tech stack
2. Confirm the module list before generating
3. Create the full `docs/` folder structure in your current working directory

Or invoke it explicitly:

```
/project-context-generator
```

## Example Output Structure

```
docs/
├── README.md
├── 00-START-HERE.md
├── 01-PRODUCT_VISION.md
├── 02-domain/
│   ├── 01-overview/          # Glossary, value proposition, stakeholders
│   └── 02-requirements/      # Personas, functional + non-functional requirements
├── 03-backlog/
│   ├── stories/              # US-001, US-002, ... with full ACs
│   └── sprints/              # Sprint plans
├── 04-architecture/
│   ├── 00-overview/          # Architecture summary, tech stack
│   ├── 02-scalability/       # Scalability strategy, caching, DB scaling
│   └── 03-decisions/         # ADR-001, ADR-002 (scalability approach)
├── 05-modules/               # One spec per module — data model, workflows, APIs
├── 06-contracts/             # OpenAPI 3.0 specs, data models
├── 07-design-system/         # Design tokens, component guidelines
├── 08-development-guides/
│   ├── 03-security/          # Auth guide, RBAC model, OWASP checklist
│   ├── 04-deployment/        # Environments, CI/CD, infrastructure, rollback
│   └── 05-observability/     # Logging standard, error handling (RFC 7807)
├── 09-testing/               # Strategy + load testing targets
└── 10-workflows/
    ├── operational-flows/    # End-to-end business process flows
    ├── user-workflows/       # Per-role workflow docs
    └── exception-scenarios/  # What happens when things go wrong
```

## Design Philosophy

- **Scalability is structural** — scale decisions are encoded into data models, architecture, and NFRs from the start, not added later
- **Security first** — OWASP Top 10 controls, JWT best practices, and RBAC/ABAC patterns are generated for every project
- **Deployable from day one** — CI/CD pipeline, environment strategy, and rollback runbook are always included
- **Cross-module flows** — operational workflows show what module specs can't: the full chain across modules

## Author

amsiam990@gmail.com

## License

MIT
