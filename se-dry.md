# DRY

The **"Don't Repeat Yourself" (DRY) principle** applies to both source code and documentation by eliminating redundancy and ensuring a single source of truth (SSOT). It states that every unit of knowledge should have a single, unambiguous representation within a system. Repetition increases the risk of inconsistencies and makes maintenance more complex, while DRY promotes clarity and efficiency.

❌Incorrect example:

```markdown
Authentication:
To access the API, send a token in the Authorization header.
(Same text appears in multiple sections.)
```

👍Correct example, DRY applied:

```markdown
See the [Authentication Guide](#authentication) for details.
```

Guidelines for DRY:

- **In code**: Use functions, modules, or inheritance to remove redundancy
- **In documentation**: Use links, templates, and auto-generated docs to avoid duplication
