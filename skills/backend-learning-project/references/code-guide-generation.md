# Code Guide Generation

## Goal

Create a beginner-friendly guide that teaches the generated project from the code outward. The guide should help a learner read the application like a working engineer, not memorize isolated syntax.

## Structure

Use this outline unless the project suggests a better one:

1. What the app does.
2. Request flow diagram.
3. Main files and responsibilities table.
4. Application entry point.
5. Routing.
6. Request parsing and validation.
7. Response generation and error handling.
8. Service/use-case layer.
9. Repository/data access layer.
10. Model/schema/data shape definitions.
11. Configuration.
12. Tests.
13. Local run and API verification.

## Explanation Pattern

For each concept:

- Start with `対象コード: <path>`.
- Include a short excerpt, not an entire file.
- Explain basic language syntax before framework behavior.
- Tie the excerpt back to the application request flow.
- Name why the design is useful in a real project.
- Make the boundary explicit when framework, language, library, and project-specific code appear together.

Use a short `境界:` block when it helps the learner distinguish responsibilities:

- Framework feature: behavior provided directly by the web framework.
- Language feature: syntax or runtime behavior from the programming language.
- Common ecosystem library: validation, ORM, HTTP client, testing, or settings library often used with the framework.
- Project-specific code: names, schemas, services, repositories, business rules, and API choices created for this learning app.

When explaining framework features, add a brief `参照:` line with the most relevant official documentation page. Keep links selective and close to the concept being explained.

## Tone

Use clear Japanese by default when the user writes in Japanese. Treat the reader as new to the language unless the user says otherwise. Avoid abstract explanations that are not grounded in a file from the project.

## Quality Bar

The guide should make these things obvious:

- Where a request enters the app.
- Where JSON is parsed and validated.
- Where business rules live.
- Where database operations live.
- How errors become HTTP responses.
- How tests exercise behavior without requiring manual server startup.
