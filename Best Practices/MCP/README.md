# MCP: Connecting AI to Everything

Model Context Protocol (MCP) is an open standard by Anthropic that enables AI to connect to external data sources and tools. OpenAI adopted it in March 2025, signaling that interoperability is becoming real.

## What MCP Enables

Without MCP, AI is limited to what's in the prompt and what it can generate. With MCP, AI can:

- **Query databases** - "Show me users who signed up last week"
- **Call APIs** - "Check the current status of our Stripe subscriptions"
- **Access file systems** - "Read the configuration from our deployment"
- **Use specialized tools** - Security scanners, linters, deployment systems

## MCP in Practice

Cursor and other tools support MCP servers that extend what AI can do:

**Database MCP:**

```
> How many active projects do we have per team?

[AI queries database via MCP]

Based on the production database:
- Team Alpha: 12 active projects
- Team Beta: 8 active projects
- Team Gamma: 23 active projects
```

**Security Scanner MCP:**

```
> Scan the new authentication code for vulnerabilities

[AI runs security scanner via MCP]

Found 2 issues:
1. SQL injection risk in /routes/users.ts line 45
2. Missing rate limiting on /api/login endpoint
```

## Setting Up MCP

MCP configuration varies by tool. Generally:

1. Install the MCP server for your data source
2. Configure credentials (securely!)
3. Add the MCP server to your tool's configuration
4. AI can now access that resource

The MCP ecosystem is growing: there are servers for databases, cloud providers, SaaS tools, and more.
