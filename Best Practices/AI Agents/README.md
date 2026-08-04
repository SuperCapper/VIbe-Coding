# AI Agents: Autonomous Execution

Agents are AI systems that execute multi-step tasks autonomously. You give them a goal, they figure out the steps, and they execute: with you reviewing the results.

## How Agents Work

Traditional vibe coding:

1. You prompt
2. AI generates code
3. You review
4. You prompt again

Agent-based vibe coding:

1. You describe the goal
2. Agent breaks it into steps
3. Agent executes each step
4. Agent handles errors and adjusts
5. You review the final result (or checkpoints along the way)

## Cursor Agent Mode

Cursor's agent mode lets the AI execute multi-file changes autonomously. Instead of reviewing each diff, you review the outcome.

**Prompt:**

> "Refactor the authentication system to use JWT instead of sessions. Update all relevant files, fix the tests, and ensure the API documentation is updated."

The agent:

1. Identifies all files that touch authentication
2. Plans the migration
3. Updates each file
4. Runs tests to verify
5. Presents you with the complete changeset

You review once, not twenty times.

## Claude Code Terminal Agent

Claude Code operates as a terminal agent by default. It can:

- Read and write files
- Run shell commands
- Execute tests
- Navigate your codebase

**Example workflow:**

```
> Add input validation to all API endpoints using Zod schemas

Claude Code:
1. Scanning /routes for API endpoints... found 12 files
2. Analyzing existing validation patterns...
3. Creating Zod schemas in /schemas/...
4. Updating endpoint handlers...
5. Running test suite...

✓ All tests pass. Created 12 new schema files, modified 12 route handlers.
```

## Windsurf Cascade

Windsurf's Cascade agent pulls context autonomously and executes extended reasoning loops. It's designed for large codebases where context is everything.

## When to Use Agents

**Good for:**

- Refactoring across many files
- Implementing features that touch multiple layers
- Migrations and updates
- Test generation

**Less good for:**

- Exploratory coding where you're figuring out what you want
- Security-sensitive changes that need human review at each step
- Situations where intermediate states matter
