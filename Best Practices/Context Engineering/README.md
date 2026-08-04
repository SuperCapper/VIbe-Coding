# Context Engineering: The Successor to Prompt Engineering

Prompt engineering is about crafting clever prompts. Context engineering is about structuring the environment so the AI can't fail.

Think of it this way: instead of "tricking" the AI with clever wording, you learn to organize documentation, schemas, and constraints so the right answer becomes obvious.

## The Components of Good Context

### 1. Project documentation that AI can read

If you want AI to understand your architecture, write it down. Not for humans, for AI.

```
# Architecture Overview

## Data Flow
1. User action triggers API call from React component
2. API route validates input with Zod schema
3. Service layer handles business logic
4. Repository layer interacts with database
5. Response returns through the same chain

## Key Patterns
- All async operations use try/catch with AppError
- User context available via useAuth() hook
- Database transactions for multi-step operations
```

### 2. Type definitions and schemas

TypeScript interfaces and Zod schemas are gold for AI. They constrain what's possible and make intent explicit.

```typescript
// This gives AI everything it needs
interface CreateProjectInput {
  name: string;              // 3-50 characters
  description?: string;      // Max 500 characters
  teamId: string;             // UUID of owning team
  visibility: 'private' | 'team' | 'public';
}
```

### 3. Example code that demonstrates patterns

When using specific APIs or frameworks, paste relevant documentation directly into the context window. Or better: reference existing code that does it right.

```
@/services/user-service.ts: this file shows our standard service pattern.
Create a similar service for projects.
```

## Context Window Management

AI context windows are large but not infinite. Be strategic:

- **Include:** Directly relevant files, type definitions, the specific code you're modifying
- **Exclude:** Entire codebases, unrelated modules, verbose logs
- **Reference:** Use @file mentions to pull in specific files rather than pasting everything

Cursor and Claude Code both handle this well: they're designed to pull relevant context automatically. But explicit references help when the AI misses something.
