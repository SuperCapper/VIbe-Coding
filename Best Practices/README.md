# The Best Practices That Actually Matter

> **TL;DR**
>
> In **Vibe Coding**, your prompt is your source code.
>
> - Be explicit about **Context** (@mention files).
> - Focus on **Behavior**, not just implementation.
> - Use **Pseudo-code** to guide complex logic.
> - Iterative prompting > One giant prompt.
> - **Tools:** Use **Cursor** and **Claude** for the best context-aware prompting.

[Placeholder]

Most "best practices" articles give you vague advice. Here's what actually moves the needle, based on what I've seen work and fail.

## 1. Define Intent Before You Prompt

Vague prompts produce vague results. Before you touch your AI tool, answer:

- What specific problem are you solving?
- What does "done" look like?
- What are the constraints (tech stack, integrations, user flow)?

Sketch a quick wireframe. Write down the user journey. The five minutes you spend here saves hours of iteration.

**Bad:** "Build a social media app"

**Good:** "Build a social feed where users can post text updates (max 280 chars), follow other users, see a chronological feed of posts from people they follow, and like/comment on posts. Use React, Tailwind, and Supabase for auth and database."

## 2. Use Rules Files

This is the technique that separates beginners from power users. Most AI coding tools support persistent context files:

- **Cursor:** `.cursorrules` or `.cursor/rules/`
- **Claude Code:** `CLAUDE.md`
- **Windsurf:** `.windsurfrules`

These files teach the AI your project conventions, coding standards, and domain context. Instead of repeating "use TypeScript strict mode" in every prompt, put it in the rules file once.

Example `.cursorrules` snippet:

```
Project: SaaS dashboard for project management
Stack: Next.js 14, TypeScript strict, Tailwind, Supabase

Conventions:
- Use server components by default, client components only when needed
- All database queries go through /lib/db.ts
- Error handling uses custom AppError class
- No console.log in production code: use structured logging
```

## 3. Follow the Research-Plan-Implement Framework

This comes from Kilo.ai's engineering team and it's gold:

**Research:** Before implementing, have the AI explore the codebase and summarize what it finds. "Read through the auth module and explain how user sessions work."

**Plan:** Create a step-by-step implementation plan. "Write out the exact files you'll modify and what changes you'll make in each." Review this plan yourself before proceeding.

**Implement:** Only after you've approved the plan do you let the AI write code.

Why this works: catching a misunderstanding during planning is 10x cheaper than debugging 500 lines of cascading errors. The AI might have a completely wrong mental model of your codebase: better to find out before it writes anything.

## 4. Use Constraint Anchoring

Constraint anchoring means setting explicit boundaries in your prompts:

- **Length constraints:** "Response should be under 50 lines of code"
- **Format constraints:** "Return only the modified function, not the entire file"
- **Style constraints:** "Follow the existing pattern in UserService.ts"
- **Scope constraints:** "Only modify the payment flow, don't touch auth"

Vague prompts get verbose, off-brand, hard-to-integrate responses. Clear constraints fix this immediately.

## 5. Test After Every Change

This sounds obvious but people skip it constantly. AI can generate code that looks flawless but has subtle bugs that only surface at runtime.

After every AI-generated change:

- Run your test suite
- Manually test the affected feature
- Check the browser console for errors
- Verify the happy path AND edge cases

The developers who thrive with vibe coding test rigorously and never ship code they don't understand.

## 6. Build Authentication Early

A mistake that costs hours of refactoring: leaving auth until the end. Adding login systems after your app is built means restructuring everything to wrap permissions around existing features.

Build auth early, even if it's just a placeholder. Your future self will thank you.

## 7. Document Your AI's Mistakes

Create a "common AI mistakes" file and reference it in new projects. Every AI has patterns it gets wrong: specific libraries it hallucinates, edge cases it misses, conventions it ignores.

Track these. Add them to your rules file. The AI will make fewer mistakes over time because you're teaching it what not to do in your specific context.
