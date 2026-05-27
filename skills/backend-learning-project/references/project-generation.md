# Project Generation

## Goal

Create a small backend API project that teaches real application structure without becoming a full product. Prefer an app that can be understood in one sitting and extended later.

## Inputs

Extract or choose:

- Language and version.
- Web framework.
- Persistence option, defaulting to SQLite or an in-memory store when that is more idiomatic for a first project.
- App theme and primary resource.
- Deployment target only when requested.

When the user does not specify a theme, use a reading tracker/bookmark API because it naturally teaches create, list, get, update, delete, filtering, validation, and a small business rule.

## Required Contents

Include:

- Application entry point.
- Route definitions.
- Handler/controller layer.
- Service/use-case layer.
- Repository/data access layer.
- Request and response data shapes.
- Configuration through environment variables when idiomatic.
- Logging or basic request diagnostics when idiomatic.
- Tests for at least the main API behavior.
- README with local setup, run commands, API examples, test commands, Docker usage when included, and a short architecture explanation.
- `docs/` guide generated after the code exists.

## API Surface

Prefer these endpoints for CRUD learning projects:

```text
GET    /health
POST   /<resources>
GET    /<resources>
GET    /<resources>/{id}
PATCH  /<resources>/{id}
DELETE /<resources>/{id}
```

Include query filtering when natural, such as `?status=done`.

## Design Constraints

- Keep dependencies modest and idiomatic for the target ecosystem.
- Do not generate a landing page for an API-only project.
- Prefer explicit code over framework magic when the goal is beginner learning.
- Keep validation and error responses visible in the code.
- Keep database setup simple and local-first.
- Include Docker only when it helps the learning goal or the user requested deployment/container practice.

## Verification

Run the stack's normal checks when available:

- Go: `go test ./...`, `gofmt`, and a compile check through tests.
- Python: `pytest`, formatter/linter if configured.
- TypeScript/Node: package test command, typecheck, and lint if configured.

If dependencies cannot be downloaded because of network restrictions, report the exact blocked command and leave clear next steps.
