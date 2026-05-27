# Gin Framework Profile

Use this profile when generating or explaining Go projects that use Gin.

## Concepts To Include

Cover these when they appear:

- `gin.Default()` and what middleware it includes.
- `gin.New()` when choosing explicit middleware.
- Route registration with `GET`, `POST`, `PATCH`, and `DELETE`.
- Route groups such as `router.Group("/reading-items")`.
- Handler functions receiving `*gin.Context`.
- `c.Param(...)` for path parameters.
- `c.Query(...)` and `c.DefaultQuery(...)` for query parameters.
- `c.ShouldBindJSON(...)` for request JSON parsing and validation.
- `c.JSON(status, body)` for JSON responses.
- `c.Status(...)` for empty responses such as `204 No Content`.
- Middleware for logging, recovery, auth, or dependency setup when included.
- Error mapping from service errors to HTTP status codes.

## Project Pattern

Keep Gin-specific code in the HTTP/handler layer. Services should not depend on `*gin.Context`; pass plain Go values into services and return domain values or errors.

Use explicit response structs when it helps learners distinguish API output from internal models.

## Testing Pattern

Use `httptest.NewRecorder()` and `http.NewRequest(...)` to test handlers or the whole router. Explain that these tests call the router in memory without starting a real server.
