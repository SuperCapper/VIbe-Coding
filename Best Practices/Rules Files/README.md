# Rules Files: Teaching AI Your Conventions

Large language models don't retain memory between completions. Every new conversation starts fresh. This is why you keep repeating "use TypeScript strict mode" or "follow our naming conventions."

Rules files solve this. They provide persistent, reusable context that gets included at the start of every AI interaction.

## Cursor: `.cursor/rules/`

Cursor deprecated the old `.cursorrules` file in favor of a `.cursor/rules/` directory containing multiple `.mdc` files. This change provides better organization: you can have separate files for different concerns.

**Example structure:**

```
.cursor/
  rules/
    general.mdc      # Overall coding style
    typescript.mdc    # TypeScript-specific rules
    react.mdc          # React patterns and conventions
    api.mdc              # API and backend conventions
```

**Example `general.mdc`:**

```
# Project Context
This is a SaaS dashboard for project management.
Stack: Next.js 14, TypeScript strict, Tailwind, Supabase.

# Coding Conventions
- Use server components by default, client components only when needed
- All database queries go through /lib/db.ts
- Error handling uses custom AppError class
- No console.log in production: use structured logging via /lib/logger.ts

# File Organization
- Components in /components, grouped by feature
- Hooks in /hooks
- Utils in /lib
- API routes in /app/api

# Testing
- Write tests for all business logic
- Use Vitest for unit tests
- E2E tests with Playwright for critical paths
```
