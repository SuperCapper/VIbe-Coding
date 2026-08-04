# How Vibe Coding Actually Works

The workflow is simpler than people make it sound.

## The Core Loop

1. **Describe what you want**: in plain language. "Build a task management app with user authentication, project creation, and a Kanban board." Or smaller: "Add a dark mode toggle to the settings page."

2. **AI generates code**: HTML, CSS, JavaScript, React components, database schemas, API routes. Depending on your tool, this might be one file or a multi-file refactor across your entire project.

3. **Look at the result**: does it work? Does the UI look right? Did the app crash? You're not reading diffs line by line. You're checking outcomes.

4. **Iterate**: "The Kanban columns should be drag-and-drop." "Add email notifications for overdue tasks." "The color scheme should be darker." Each prompt refines what you have.

5. **When things break, paste the error**: the Karpathy move. Copy the error message, paste it into the chat, let the AI figure out what went wrong.

The conversation becomes your source code. The actual files are almost a byproduct.
