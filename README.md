# How Vibe Coding Actually Works

The workflow is simpler than people make it sound.

## The Core Loop

1. **Describe what you want**: in plain language. "Build a task management app with user authentication, project creation, and a Kanban board." Or smaller: "Add a dark mode toggle to the settings page."

2. **AI generates code**: HTML, CSS, JavaScript, React components, database schemas, API routes. Depending on your tool, this might be one file or a multi-file refactor across your entire project.

3. **Look at the result**: does it work? Does the UI look right? Did the app crash? You're not reading diffs line by line. You're checking outcomes.

4. **Iterate**: "The Kanban columns should be drag-and-drop." "Add email notifications for overdue tasks." "The color scheme should be darker." Each prompt refines what you have.

5. **When things break, paste the error**: the Karpathy move. Copy the error message, paste it into the chat, let the AI figure out what went wrong.

The conversation becomes your source code. The actual files are almost a byproduct.

## When to Intervene vs. Let It Flow

The art is knowing when to guide versus when to accept. Some rules I've found useful:

- **Let it flow** when you're scaffolding, exploring ideas, or building UI components
- **Intervene** when you're touching auth, payments, data handling, or anything security-adjacent
- **Always review** database schemas, API permissions, and anything that touches user data

The developers who get burned are the ones who vibe code their authentication system. Don't be that person.

## Good Use Cases

- **Prototypes and MVPs** - speed matters more than perfection
- **Internal tools** - lower stakes, faster iteration
- **Weekend projects** - Karpathy's original use case
- **Learning** - great way to understand how systems fit together
- **UI components** - generating visual elements from descriptions
- **Boilerplate** - scaffolding that would otherwise be tedious
- **Exploring ideas** - testing whether something is even possible

## Bad Use Cases

- **Security-critical code** - auth, encryption, payment processing
- **Performance-critical code** - AI generates correct but not optimal code
- **Compliance-heavy domains** - healthcare, finance, legal (HIPAA, SOC2, etc.)
- **Long-term production systems** - maintained by teams over years
- **Anything you can't explain** - if you can't debug it, you shouldn't ship it

## The Experienced Developer Advantage

Reddit's consensus on r/programming is consistent: experienced programmers plus vibe coding equals superpowers. Inexperienced people plus vibe coding equals projects that fail when they hit complexity.

The best vibe coders understand architecture, can spot bad AI output, and know when to intervene. They use AI to skip the tedious parts while maintaining control over the decisions that matter.

If you don't understand what good code looks like, you can't evaluate whether the AI produced good code.

## When to Stop Vibing and Read the Code

Pure vibe coding and responsible AI-assisted development are different modes, and knowing when to switch is the actual skill. My checklist for when the accept-all phase is over:

- You're about to deploy to production or take real users
- The code touches secrets, auth, payments, or personal data
- Someone else (or a team) will have to maintain it
- You couldn't explain a core function to another person if they asked
- The same bug has come back three times and the AI keeps "fixing" it

Hit any of these and the mode changes: read the diffs, ask the AI to explain the architecture, write tests. And if a vibe-coded prototype is getting handed to professional engineers, give them the prompt history and a written walkthrough of what you think it does. The handoff goes much smoother when they're not reverse-engineering a mystery.
