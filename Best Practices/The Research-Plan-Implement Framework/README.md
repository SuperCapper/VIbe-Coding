# The Research-Plan-Implement Framework

This framework comes from professional AI-assisted development workflows. It catches mistakes early: before they cascade into hundreds of lines of broken code.

## Phase 1: Research

Before implementing anything complex, have the AI explore the codebase.

**Prompt:**

> "I want to add a notification system. Before we implement anything, analyze the codebase:
>
> - How do we currently handle real-time updates?
> - Where should notification preferences be stored?
> - What existing patterns should we follow? Summarize your findings before proposing any code."

The AI reads your code, understands the context, and surfaces assumptions. You catch misunderstandings before they become bugs.

## Phase 2: Plan

Once the AI understands the codebase, have it create a step-by-step plan.

**Prompt:**

> "Based on your analysis, create a detailed implementation plan for the notification system:
>
> 1. List each file that needs to be created or modified
> 2. Describe the changes for each file
> 3. Identify any dependencies or ordering constraints
> 4. Note potential risks or edge cases
>
> Don't write any code yet. Just the plan."

Review this plan carefully. Does it make sense? Did it miss anything? Is the approach what you expected?

## Phase 3: Implement

Only after you've approved the plan do you let the AI write code.

**Prompt:**

> "The plan looks good. Implement step 1: create the notification model and database migration."

If something goes wrong, you know exactly where in the plan it diverged. You can course-correct early.

## Why This Works

The cost of catching a misunderstanding:

- **During Research:** ~30 seconds to clarify
- **During Planning:** ~2 minutes to adjust the plan
- **During Implementation:** ~20 minutes to debug and refactor
- **After Deployment:** Hours to days

The Research-Plan-Implement framework front-loads the cheap mistakes and prevents the expensive ones.
