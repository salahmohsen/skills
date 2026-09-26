# Quest design

How to turn "I want to learn X" into projects that actually teach.

## The coupling rule

A tool learned alone evaporates. A tool that collides with your stack sticks.

Every quest must force the learn-target to work with **≥2 pieces the learner already has**. The friction at the seams is the lesson.

| Weak quest | Coupled quest |
|---|---|
| Build a login form | Login form that stores users in Prisma and guards a route in Next.js middleware |
| Learn Prisma migrations | Add a `Todo` model, migrate, and render it from a Server Component |
| Try better-auth | Role-based sessions where a provider sees patients and a patient sees only their own record |

The weak version teaches syntax. The coupled version teaches wiring — the part that survives.

## Quest anatomy

The card lives in [SKILL §3](../SKILL.md). Three quality bars:

- **One vertical slice.** Front → API → DB. Never a disconnected tour.
- **Stretch is one thing.** Two stretches = the learner stalls.
- **Done is checkable by a machine.** "Logged-out user hits `/dashboard` → redirected", not "auth works".

## Exactly three

Three quests. Enough choice to feel agentic, few enough to avoid paralysis. More options lower the odds any is chosen.

## Forking

After showing the three, invite edits:

- swap the stretch of one with another's
- tighten or loosen the done line
- rename it

The learner owning the quest is the first dopamine hit. Let them spend it.

## JD mode

When a job description is present:

1. Extract role, languages, frameworks, the product domain.
2. Map the required stack against what the learner already knows → find the gaps.
3. Derive quests from the company's **real feature surface**, not generic tutorials.

Example — a telehealth company needing Next.js + tRPC + Prisma:

```
Quest: Multi-tenant patients
Learn:   scoping every query by tenant
Touches: Prisma (models) + tRPC (procedures) + Next.js (session)
Stretch: a second org that must never see the first's data
Done:    querying as org B returns zero of org A's rows
```

Now prep reads like a ticket from that team.

## ctx7

Before designing, pull current docs:

```bash
npx ctx7@latest library "<name>" "<goal>"
npx ctx7@latest docs <id> "<question>"
```

Design quests against what the docs actually say. If ctx7 is unavailable, proceed and tell the learner docs weren't verified.

## Worked example

Learner: mid-senior frontend dev, fluent in Drizzle, learning Prisma.

```
Quest: Todo, but the Prisma way
Learn:   Prisma's schema → migrate → generate cycle
Touches: Next.js (Server Components) + Postgres
Stretch: a relation (User → Todo) with cascade delete
Done:    a todo renders on the page from a migrated table

Quest: Server Actions with Prisma
Learn:   why Prisma is server-only
Touches: Next.js Client Component + Server Action
Stretch: revalidate so the list updates without a reload
Done:    form submit persists and the list reflects it

Quest: Swap Drizzle for Prisma
Learn:   translating mental models, not syntax
Touches: the existing Drizzle schema + query call sites
Stretch: keep both clients alive behind one interface
Done:    all reads go through Prisma, Drizzle removed
```

Each quest drills one idea, collides with the real stack, and ends on a fact.
