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

## Getting Started: A Walkthrough

### Step 1: Choose Your Tool

Different tools work better for different people. Here's the honest breakdown for May 2026.

### Step 2: Write Your First Prompt

Your prompt is your blueprint. Better prompts produce better results.

**The Anatomy of a Good Prompt**

A good vibe coding prompt answers these questions:

1. **What is this?** - The type of app or feature
2. **Who is it for?** - The user and their context
3. **What does it do?** - The core functionality
4. **How should it look?** - Style preferences (optional but helpful)

**Bad Prompt vs. Good Prompt**

Bad prompt:

> "Make me an app"

This gives the AI nothing to work with. You'll get something generic and probably not what you wanted.

Good prompt:

> "Build an expense tracker for freelancers. It should have:
>
> - A form to add expenses with amount, category, and date
> - A dashboard showing total expenses by month
> - Categories: Travel, Software, Office, Marketing, Other
> - Clean, minimal design with a dark mode option
> - Use Tailwind CSS for styling"

### Step 3: Generate Your First Version

Open your chosen tool. Paste your prompt. Hit generate.

**What happens next:**

- The AI analyzes your description
- It creates the file structure, components, and styling
- You see a preview of your app (usually within 30 seconds to 2 minutes)

**What to expect:**

- About 80% of what you asked for will be right
- Some things will be off: that's normal
- The layout might not be exactly what you imagined
- Some features might be missing or interpreted differently

Don't panic. The first generation is a starting point, not the final product. The real magic happens in iteration.

**The 80% Rule**

Your first generation will be roughly 80% correct. That's actually great: it means you have a foundation to build on. Traditional development would have taken hours to reach this point.

The remaining 20% comes from iteration. That's Step 4.

### Step 4: Iterate With Conversational Edits

This is where beginners make the most progress, and where most get the workflow wrong.

**The Key Insight: Small Prompts Beat Big Prompts**

Don't try to fix everything in one message. Break it down.

Instead of:

> "The header is too big, the buttons are the wrong color, the spacing is off, I wanted the sidebar on the left not the right, and can you add a search bar and make it responsive?"

Do this:

> "Make the header smaller: about half the current height."

Then:

> "Change the button colors to blue."

Then:

> "Move the sidebar to the left side."

### The Feedback Loop

The vibe coding workflow is a loop:

1. Prompt
2. See result
3. Identify one thing to change
4. Prompt again
5. Repeat until satisfied

Most successful vibe coders do 10-20 iterations on a single feature. That's normal. Each iteration takes seconds.

### Step 5: Add Logic and Functionality

Once the layout looks right, you add the behaviors that make the app useful.

**Common Beginner Features**

Forms and inputs:

- "Add a form with fields for name, email, and message"
- "Validate the email field before allowing submission"
- "Show a success message after the form is submitted"

Data operations:

- "Calculate and display the total at the bottom"
- "Filter the list to show only items marked as 'active'"
- "Sort by price from low to high"

User interactions:

- "Add a confirmation dialog before deleting an item"
- "Show a tooltip when hovering over the info icon"
- "Collapse the sidebar when clicking outside of it"

**How to Ask for Specific Behaviors**

Be precise about triggers and outcomes:

**Not great:** "Make the delete button work"

**Better:** "When the user clicks the delete button, show a confirmation dialog. If they confirm, remove the item from the list and show a toast notification saying 'Item deleted'."

The more specific you are about what triggers an action and what the result should be, the better the output.

### Step 6: Polish the Design

Functionality first, then aesthetics. Once everything works, make it look good.

**Layout Polish**

- "Increase the spacing between sections"
- "Make the cards all the same height"
- "Add a subtle shadow to the card elements"
- "Use a consistent border radius across all elements: 8px"

**Color and Typography**

- "Use a warmer color palette: soft whites and warm grays"
- "Make the headings darker and increase the font weight"
- "Add a subtle gradient to the primary button"

**Mobile Responsiveness**

This one matters. Always ask:

- "Make the layout responsive: stack the columns on mobile"
- "Hide the sidebar on screens smaller than 768px and add a hamburger menu"
- "Increase the button size on mobile for easier tapping"

Test on your phone. If it looks broken, tell the AI what's wrong and how to fix it.

### Step 7: Audit, Then Deploy

You've built something. Before you put it on the internet, run a 30-minute security pass. AI-generated code has predictable gaps and you can catch most of them without being a security expert.

**Before-you-ship checklist (5 minutes per item):**

1. Are there any API keys, tokens, or `.env` values committed to git? Search the repo for "sk-", "API_KEY", "SECRET".
2. If you're using Supabase, is Row Level Security enabled on every table?
3. Does every API route check that the request is authenticated?
4. Is there a rate limit on the routes that call an LLM (otherwise one user can rack up a $5k bill)?
5. Is CORS restricted to your domain, not `*`?

If anything from the checklist trips you up, that's the point at which inheriting some help is cheap.

Once you're clean, deploy.
