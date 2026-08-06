# Vibe Coding Workflows

## What Makes a Vibe Coding Workflow

A vibe coding workflow is a repeatable process for turning an idea into working software using AI tools. It's not "open Cursor and start typing prompts." It's a structured sequence with clear stages.

Every effective vibe coding workflow follows the same core loop:

**Intent → Spec → Prompt → Generate → Review → Iterate → Ship**

The difference between workflows is which tools handle each stage, how much review happens, and how fast you move through the loop. A solo developer prototyping a weekend project might blast through the loop in minutes. A team shipping production code might spend days on the spec and review stages.

What separates productive vibe coders from frustrated ones isn't the tool: it's having a process. As Andrew Ng put it: vibe coding "requires structuring your work, refining your prompts, and having a systematic process."

## The 5 Stages of Every Vibe Coding Workflow

Before jumping into specific workflows, here's the universal framework. Every workflow in this guide maps to these five stages, just with different tools and time allocations.

| Stage | What You Do | What AI Does | Key Prompt Pattern |
|---|---|---|---|
| **1. Define** | Write a spec: features, constraints, users, edge cases | Help brainstorm requirements, identify gaps | "I'm building X for Y users. Help me identify the core features and edge cases." |
| **2. Scaffold** | Choose tech stack, review project structure | Generate boilerplate, directory structure, config | "Set up a Next.js project with Supabase auth and Tailwind. Show the file structure first." |
| **3. Build** | Prompt feature-by-feature, review each output | Generate components, logic, API routes | "Add a dashboard page that shows user stats from the /api/stats endpoint." |
| **4. Debug & Test** | Paste errors, describe broken behavior | Diagnose issues, suggest fixes, write tests | "This error appears when I click submit: [paste error]. The form should save to the users table." |
| **5. Ship** | Configure deployment, review final output | Generate deploy configs, environment setup | "Create a Vercel deployment config for this project with these environment variables." |

The time split varies. For a prototype, you might spend 10% on Define and 60% on Build. For a production feature, flip that: 40% on Define and Scaffold, 30% on Build, 30% on Debug & Test.
