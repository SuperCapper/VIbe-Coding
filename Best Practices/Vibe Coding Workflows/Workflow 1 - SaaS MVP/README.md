# Workflow 1: Solo Developer Building a SaaS MVP

**Best for:** Developers who can read code, building MVPs and side projects.

**Tool stack:** Cursor (IDE) + Supabase (backend) + Vercel (deploy)

**Estimated time:** 4-8 hours from idea to deployed MVP

## Stage 1: Define (30 min)

Start a new chat in Cursor Composer. Don't ask it to write code yet. Use the first conversation to nail down the spec.

```
I'm building a habit tracker SaaS. Target users are people who want a simple, fast daily check-in, not a complex life management tool.

Core features:
- User auth (email + Google)
- Daily habit check-in (checkboxes)
- 7-day and 30-day streak tracking
- Simple dashboard with completion rate

Tech stack: Next.js 14, Supabase (auth + db), Tailwind CSS, Vercel deploy.

Before writing any code, outline the database schema, page structure, and key API routes. I want to review the architecture first.
```

Review what comes back. Look for missing tables, unclear routes, or features that got over-engineered. Push back on anything that feels too complex for an MVP.

## Stage 2: Scaffold (20 min)

Once the architecture looks right, ask Cursor to generate the project skeleton.

```
Create the project structure based on the architecture we discussed.
Start with:
1. Supabase schema (SQL for the habits and check_ins tables)
2. Next.js project with the page routes
3. Supabase client setup with environment variables
4. Auth configuration (email + Google OAuth)

Don't build features yet, just the scaffold.
```

**Checkpoint:** Run the project. Does it start? Can you see the login page? Does Supabase connect? Don't move forward until the scaffold runs clean.

## Stage 3: Build (2-4 hours)

Build feature by feature. One prompt per feature. Review and test each before moving to the next.

```
Build the daily check-in page:
- Fetch the user's habits from Supabase
- Show each habit as a checkbox
- When checked, insert a record into check_ins with today's date
- Show a simple streak count next to each habit
- Use Tailwind for styling: keep it minimal
```

After each feature, commit your code. This isn't optional. If you can point to the exact commit that broke something, the AI can fix it much faster.

```
git add . && git commit -m "feat: daily check-in page with streak count"
```

## Stage 4: Debug & Test (1-2 hours)

When something breaks (it will), paste the full error into Cursor:

```
When I check a habit, I get this error in the console:

[paste full error stack trace]

The check_in should be inserted into the check_ins table with the user_id, habit_id, and today's date. The habit row should show the updated streak count after checking.
```

Context helps. Don't just paste the error: describe what *should* happen. The AI fixes things faster when it knows the intent, not just the symptom.

## Stage 5: Ship (30 min)

```
Create a Vercel deployment configuration for this project.
I need:
- Environment variables for NEXT_PUBLIC_SUPABASE_URL and NEXT_PUBLIC_SUPABASE_ANON_KEY
- A vercel.json if needed
- Instructions for connecting the GitHub repo to Vercel
```

**Final checkpoint:** Deploy to a preview URL. Test the full flow: sign up → create habits → check in → see streak. If it works, promote to production.

## Cost for This Workflow

Cursor Pro at $20/month, Supabase free tier, Vercel free tier. Total: $20/month to start.
