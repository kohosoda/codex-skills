---
name: backend-learning-project
description: Create small backend application projects for learning any language and web framework, then generate beginner-friendly code-reading guides from the generated project. Use when the user wants to learn a backend language/framework by building a new practical API project, wants a project like a FastAPI/Gin/Express learning repo, wants code explained from basic syntax through framework concepts, or wants reusable Codex guidance for creating language-specific learning projects.
---

# Backend Learning Project

## Overview

Use this skill to create a compact, practical backend API project for learning a language and framework, then turn the project into a code-reading guide. Keep the project small enough to finish in one session but realistic enough to teach routing, validation, application layers, persistence, tests, Docker, and local operation.

## Workflow

1. Identify the target language, framework, persistence option, and app theme from the user request. If any are missing, choose conservative defaults and state them briefly before implementation.
2. Read the relevant profile files:
   - Language profile: `references/language-profiles/<language>.md` when it exists.
   - Framework profile: `references/framework-profiles/<framework>.md` when it exists.
   - If no profile exists, proceed with general backend conventions and create an opportunity to add a profile later.
3. Use `references/project-generation.md` to design and implement the project.
4. Run the project checks that fit the stack, such as unit tests, formatting, linting, or a smoke test.
5. Use `references/code-guide-generation.md` to create a beginner-oriented guide under `docs/`, such as `docs/gin-guide.md` or `docs/fastapi-guide.md`.
6. Finish with the created files, verification results, and the local run command.

## Project Shape

Prefer a CRUD API around one clear domain object, such as reading items, bookmarks, tasks, notes, recipes, or expenses. Include one behavior that is more than plain CRUD, such as fallback title generation, status transitions, filtering, validation, or a small external HTTP lookup.

Use a layered structure when idiomatic for the framework:

```text
HTTP/router/handler
  -> service/use case
  -> repository/data access
  -> database/storage
```

Keep the code intentionally readable. Avoid clever abstractions, large generators, and broad scaffolds that hide the concepts the user is trying to learn.

## Guide Style

Generate the learning guide from the actual code that exists in the project. Use this teaching pattern repeatedly:

1. Name the target file.
2. Show a short code excerpt.
3. Explain language syntax first when the user is likely to be new to the language.
4. Explain the framework concept.
5. Explain the role this code plays in the request flow.

For Go, give extra attention to basic syntax before explaining Gin behavior. For other languages, follow the same principle using the relevant language profile.

## Reference Files

- `references/project-generation.md`: implementation checklist for new projects.
- `references/code-guide-generation.md`: documentation checklist and guide structure.
- `references/language-profiles/go.md`: Go syntax topics to explain in generated guides.
- `references/framework-profiles/gin.md`: Gin concepts and project patterns to include.
