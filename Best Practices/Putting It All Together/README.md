# Scenario: Adding a Reporting Feature

## 1. Set up context (Rules files)

Your `.cursor/rules/reports.mdc`:

```
# Reporting Module
- Reports use the existing ChartJS setup in /lib/charts.ts
- Data aggregation happens in /services/analytics.ts
- All date ranges use UTC and dayjs library
- Export formats: PDF (via react-pdf), CSV, JSON
```

## 2. Research the codebase

> "I want to add a weekly summary report. Before implementing, analyze:
>
> - How do existing reports work?
> - Where is analytics data aggregated?
> - What export patterns exist?"

Review the AI's analysis. Correct any misunderstandings.

## 3. Create a plan

> "Create an implementation plan for the weekly summary report. Include file changes, new components, and API endpoints needed."

Review and approve the plan.

## 4. Implement with agents

> "Implement step 1: create the data aggregation service for weekly summaries."

Let the agent execute. Review the result.

## 5. Use MCP for verification

> "Query the test database and verify the weekly aggregation is calculating correctly for the last 4 weeks."

AI connects to database, runs verification, reports results.

## 6. Security review

> "Scan the new report endpoints for security issues."

AI runs security scanner, surfaces any concerns.

This workflow is faster than basic vibe coding AND produces better results. Each technique compounds the others.
