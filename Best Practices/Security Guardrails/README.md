# Security Guardrails For Agents

With great power comes great responsibility. Agents with database access and file system permissions can do real damage if misconfigured.

## Essential Guardrails

### 1. Permission boundaries

Limit what agents can access:

- Read-only database access for queries (no mutations)
- Specific directories only (not entire filesystem)
- Sandbox environments for testing

### 2. Human-in-the-loop for critical actions

Some things should always require human approval:

- Database migrations
- Deployment to production
- Deleting user data
- Security-sensitive changes

### 3. Audit logging

Log everything agents do:

- What was requested
- What actions were taken
- What files were modified
- What external calls were made

### 4. Input validation

Even AI-generated code needs validation:

- Zod schemas for runtime type checking
- Sanitize user inputs
- Validate before database operations

## The Principle

Trust but verify. Agents are powerful, but they're not infallible. Build systems that:

- Give agents enough permission to be useful
- Restrict permissions enough to prevent disasters
- Log everything for accountability
- Require human approval for irreversible actions
