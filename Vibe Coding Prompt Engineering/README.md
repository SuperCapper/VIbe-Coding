# The 5 Golden Rules of Vibe Prompting

## 1. Context is King (@Files)

Most AI failures happen because the AI doesn't know what you're talking about.

- **Bad:** "Fix the bug in the login."
- **Good:** "@auth.ts @login-form.tsx Fix the bug where the user session isn't persisting after refresh."

## 2. Describe the "Why" and "What", not just "How"

Give the AI the goal. It might find a better way than you.

- **Prompt:** "I need a way for users to filter this list. It should feel instant, like Algolia."

## 3. Use "Chain of Thought"

For complex tasks, ask the AI to plan first.

- **Prompt:** "I want to migrate this page to Server Components. First, analyze the dependencies. Then, propose a plan. Finally, execute step 1."

## 4. The "Role" Hack

Tell the AI who it is.

- **Prompt:** "Act as a Senior React Engineer obsessed with performance. Refactor this component."

## 5. Iteration is Key

Don't try to do everything in one prompt.

1. "Scaffold the basic UI."
2. "Add the API connection."
3. "Style it to match our design system."

# Advanced Techniques

## The "Reference" Prompt

Paste a snippet of code you like and say: *"Write the new component using this coding style and pattern."*

## The "Error" Prompt

Don't just paste the error. Paste the error AND the code that caused it. *"@api.ts I'm getting this 500 error when I submit the form. Here is the log."*

# Tools for Better Prompting

The tool you use matters.

- **Cursor:** Best for referencing specific files and docs in the Frontend.
- **Claude Code:** Best for referencing specific files and docs in the Backend.
- **Devin:** Great for "deep context" where it finds relevant files for you.
