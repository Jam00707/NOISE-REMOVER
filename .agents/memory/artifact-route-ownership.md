---
name: Artifact route ownership
description: Path collisions between the shared API service and web artifact routes.
---

Shared service routes take precedence over web artifact routes in the preview proxy. A frontend page named API must not use `/api` when the workspace API service already owns that path; use a distinct route such as `/api-docs` and update all navigation links.

**Why:** The `/api` path was served by the API service, so the frontend's API documentation page returned a plain 404 even though the React route existed.

**How to apply:** Before adding a web route, check existing artifact service paths and avoid reusing reserved prefixes. Verify the route through the proxied preview URL, not only the Vite dev server.