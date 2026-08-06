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

## Breakout: The Framework-First Workflow (Wasp + Cursor)

There's a variant of the solo developer workflow worth calling out separately: using an opinionated full-stack framework alongside your AI IDE.

Wasp is an open-source framework that lets you define your app's structure in a declarative `.wasp` config file: routes, auth, database models, server actions, and it generates the React frontend, Node.js backend, and Prisma ORM layer for you. When you pair this with Cursor or another AI IDE, something interesting happens: the AI isn't generating arbitrary full-stack code from scratch. It's working within a framework's conventions, which means fewer hallucinated patterns and more consistent output.

The workflow looks like this:

**1. Define your app in the `.wasp` file.** This is where you declare pages, routes, auth methods, and database entities. It's a short config: maybe 30-50 lines for an MVP.

```
app HabitTracker {
  wasp: { version: "^0.15.0" },
  title: "HabitTracker",
  auth: {
    userEntity: User,
    methods: { google: {}, email: {} }
  }
}

entity Habit {=psl
  id        Int      @id @default(autoincrement())
  name      String
  userId    Int
  user      User     @relation(fields: [userId], references: [id])
  checkIns  CheckIn[]
psl=}

route DashboardRoute { path: "/dashboard", to: DashboardPage }
page DashboardPage { component: import { Dashboard } from "@src/pages/Dashboard" }
```

**2. Let AI handle the page components and server logic.** Once the framework structure exists, prompt Cursor to build within it:

```
Using the Wasp entities defined in main.wasp, build the Dashboard page component at src/pages/Dashboard.tsx. It should:
- Fetch all habits for the current user using a Wasp query
- Display each habit with a checkbox for today's check-in
- Show a 7-day streak count next to each habit
- Use the Wasp useQuery hook for data fetching
```

**3. The framework catches mistakes the AI makes.** If the AI generates a query that doesn't match your Wasp entities, the compiler tells you immediately. You're not hunting through a custom backend to figure out why something broke: the framework's type system flags it.

**Why this matters for vibe coding:** The biggest risk in Workflow 1 is that the AI generates a sprawling custom backend with inconsistent patterns. A framework like Wasp acts as a structural guardrail. The AI fills in the details, but the architecture stays clean because the framework enforces it. This is particularly useful if you're building something you plan to maintain beyond the prototype stage.

**Cost:** Wasp is free and open-source. Combined with Cursor Pro ($20/month), Supabase free tier, and a hosting provider, you're at the same $20/month as Workflow 1 but with a more maintainable output.
