# FastAPI Framework Profile

Use this profile when generating or explaining Python projects that use FastAPI.

## Concepts To Include

Cover these when they appear:

- `FastAPI(...)` for creating the app.
- `lifespan` for startup/shutdown behavior.
- `app.include_router(...)` for registering routers.
- `APIRouter(...)`, `prefix`, and `tags` for grouping API routes.
- Path operation decorators such as `@router.get(...)`, `@router.post(...)`, `@router.patch(...)`, and `@router.delete(...)`.
- Path parameters such as `/{item_id}` and matching function argument names.
- Query parameters inferred from simple function arguments.
- Request bodies inferred from Pydantic `BaseModel` subclasses.
- `response_model=...` for response documentation, serialization, and filtering.
- `Depends(...)` and `Annotated[...]` for dependency injection.
- Dependencies with `yield` for per-request setup and cleanup.
- `HTTPException` for mapping application errors to HTTP responses.
- `status.HTTP_...` and `Response` for explicit HTTP status codes and empty responses.
- `async def`, `await`, and the difference between Python async syntax and FastAPI behavior.
- Automatic OpenAPI and Swagger UI documentation.
- `TestClient` and `app.dependency_overrides` for tests.

## Boundary Guidance

Be explicit about what belongs to FastAPI and what does not.

- FastAPI features: `FastAPI`, `APIRouter`, path operation decorators, `response_model`, `Depends`, `HTTPException`, `Response`, `status`, `TestClient`, `dependency_overrides`, generated OpenAPI/Swagger UI.
- Python features FastAPI reads or supports: type hints, `Annotated`, `Enum`/`StrEnum`, `async def`, `await`, function defaults such as `None`.
- Common libraries used with FastAPI: Pydantic models and fields, SQLAlchemy models/sessions/queries, Pydantic Settings, httpx clients, pytest fixtures.
- Project-specific code: concrete schema names such as `ReadingItemCreate`, service/repository classes, domain enum values, URL paths, business rules, fallback behavior, and error class names.

Avoid phrasing that makes project-defined Pydantic models sound like built-in Pydantic classes. For example, say "`ReadingItemCreate` is a project-defined Pydantic model" rather than "Pydantic's `ReadingItemCreate`".

## Request Body Explanation

When explaining a handler argument such as:

```python
payload: ReadingItemCreate
```

make these points clear:

- The argument name `payload` is not special.
- The argument position is not what makes it a request body.
- FastAPI sees that `ReadingItemCreate` is a Pydantic `BaseModel` subclass and treats it as request body data.
- `Depends(...)` marks an argument as dependency injection instead of request body data.
- Path parameter names must match placeholders such as `{item_id}`.

## Project Pattern

Keep FastAPI-specific code in the API/router layer. Services should not depend on FastAPI request objects or raise `HTTPException` unless the project intentionally chooses that simpler pattern for a tiny example. Prefer passing plain Python values or Pydantic input models into services and returning domain/ORM objects or project-specific errors.

Use separate Pydantic schemas for create, update, and read responses when it helps learners see why API input shape differs from API output shape. Explain that this split is common but not required by FastAPI.

Use separate SQLAlchemy models for database tables when persistence is included. Explain that SQLAlchemy is not FastAPI, even though FastAPI's response handling can serialize ORM objects through Pydantic configuration such as `from_attributes=True`.

## Official Docs References

Add concise `参照:` lines near relevant concepts. Prefer these official FastAPI links:

- App basics: https://fastapi.tiangolo.com/tutorial/first-steps/
- Lifespan: https://fastapi.tiangolo.com/advanced/events/
- Larger apps and routers: https://fastapi.tiangolo.com/tutorial/bigger-applications/
- Path parameters: https://fastapi.tiangolo.com/tutorial/path-params/
- Query parameters: https://fastapi.tiangolo.com/tutorial/query-params/
- Request body: https://fastapi.tiangolo.com/tutorial/body/
- Body fields: https://fastapi.tiangolo.com/tutorial/body-fields/
- Response model: https://fastapi.tiangolo.com/tutorial/response-model/
- Extra models: https://fastapi.tiangolo.com/tutorial/extra-models/
- Dependencies: https://fastapi.tiangolo.com/tutorial/dependencies/
- Sub-dependencies: https://fastapi.tiangolo.com/tutorial/dependencies/sub-dependencies/
- Dependencies with yield: https://fastapi.tiangolo.com/tutorial/dependencies/dependencies-with-yield/
- Handling errors: https://fastapi.tiangolo.com/tutorial/handling-errors/
- Response status code: https://fastapi.tiangolo.com/tutorial/response-status-code/
- Async: https://fastapi.tiangolo.com/async/
- SQL databases: https://fastapi.tiangolo.com/tutorial/sql-databases/
- Settings: https://fastapi.tiangolo.com/advanced/settings/
- Testing: https://fastapi.tiangolo.com/tutorial/testing/
- Testing dependency overrides: https://fastapi.tiangolo.com/advanced/testing-dependencies/
- Metadata and docs URLs: https://fastapi.tiangolo.com/tutorial/metadata/

## Testing Pattern

Use `fastapi.testclient.TestClient` to test the app in memory without starting a real server. Use `app.dependency_overrides` to replace database sessions, services, or external clients with test doubles. Explain which part is FastAPI's override feature and which part is project-specific test setup.
