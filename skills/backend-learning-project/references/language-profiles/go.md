# Go Language Profile

Use this profile when generating or explaining Go backend projects. Assume the learner may be new to Go and explain syntax directly from the project code before discussing framework behavior.

## Syntax To Explain

Cover these when they appear:

- `package main` and package boundaries.
- `import` blocks and module paths.
- `go.mod`, module names, and dependency versions.
- `func`, parameters, return values, and multiple return values.
- `main()` as the application entry point.
- `struct` definitions and field tags such as `json:"title"`.
- Pointers such as `*Service`, when mutation/shared dependencies are intended.
- Method receivers such as `func (s *Service) Create(...)`.
- Interfaces as small contracts between layers.
- `context.Context` for request lifetime, cancellation, and database calls.
- `err != nil` as Go's explicit error handling style.
- `defer` for cleanup.
- Short variable declaration `:=` versus `var`.
- Slices such as `[]ReadingItem`.
- Maps such as `map[string]string`.
- Exported names with uppercase first letters and unexported names with lowercase first letters.
- `time.Time` for timestamps.

## Project Guidance

Prefer this shape for a first Go backend project:

```text
cmd/api/main.go
internal/config
internal/http
internal/handler
internal/service
internal/repository
internal/model
```

Use dependency injection through constructors, for example `NewService(repository)`, instead of global mutable state. Keep interfaces close to the consumer when useful, especially between service and repository layers.

## Testing Guidance

Use Go's standard `testing` package where possible. For HTTP APIs, use `net/http/httptest`. Explain tests as normal Go functions named `TestXxx`.
