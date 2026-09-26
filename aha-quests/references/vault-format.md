# Vault format

Everything the skill creates lives in `aha/` at the project root.

## Layout

```
aha/
├── index.md
├── quest.md
├── learner.md
└── tasks/
    ├── 01-<slug>.md
    └── 02-<slug>.md
```

Plain `[[wikilinks]]` only. Opening `index.md` in Obsidian navigates to every task on click. No Dataview, no plugins, no setup.

## index.md

```md
---
type: index
quest: <quest name>
status: doing
---

# <Quest name>

- [[quest]] — the goal and why
- [[learner]] — your profile and settings

## Tasks

- [[tasks/01-scaffold]] — todo
- [[tasks/02-auth]] — doing
- [[tasks/03-roles]] — todo
```

Update the status word as tasks move. Keep it the single map.

## quest.md

```md
---
type: quest
status: doing
---

# <Quest name>

**Learn:** <one thing>
**Touches:** <stack pieces>
**Stretch:** <one notch past comfort>
**Done:** <one checkable sentence>

## Why

<one or two lines tying the tasks back to the done line>
```

Every task must trace back to the done line here. If a task doesn't serve the goal, cut it.

## learner.md

Written and updated by the agent. Silent — never narrated.

```md
---
type: learner
---

## You

level: <inferred>
style: <how they learn>
tone: <what lands, what doesn't>
flow: <when they lose steam>
weak spots: <updated from observations>
wins: <dated, morale fuel>

## Stack

role: <title>
lang: <language>
frontend: <frameworks>
backend: <frameworks, ORMs>
wants: <learn-target>

## Settings

task size: step        # DEFAULT granularity (micro | step | slice); §5 asks per step
checks: ai-runs        # ai-runs | user-runs | ask-each-time
why-question: per-task # per-task | off
```

Tone comes from **behavior**, not questions. If the learner curses when stuck, stay blunt. If they go quiet, stop cheerleading.

## tasks/NN-slug.md

```md
---
type: task
status: todo        # todo | doing | done
check-in: explain   # explain | none
size: step          # micro | step | slice — asked at step start (SKILL §5)
---

# <Task name>

## Mission

<what to build. No answer, no steps.>

## Done when

<one checkable sentence>

## Mentor notes

<agent writes here after observing the attempt>

✓ <what's right>
△ <gap or smell>
→ <next nudge>
```

### check-in flag

The agent sets it when writing the task:

- `explain` — task has real design choices (state, data flow, boundaries). Agent asks one "why" question after.
- `none` — mechanical task (config, boilerplate, wiring). Doing it already proves it. Skip the question.

The learner can override.

## gitignore routine

Run on first creation, every time, idempotently.

1. Not a git repo → skip gitignore entirely; still create `aha/`.
2. No `.gitignore` → create one containing `aha/`.
3. `.gitignore` exists, no `aha/` entry → append `aha/`.
4. `.gitignore` already lists `aha/` → do nothing.
5. `aha/` exists but is git-**tracked** → leave it. Never gitignore a file the learner deliberately tracks. One line if unsure: *"aha/ is tracked — keep it tracked?"*

Guiding rule: act on new or absent. Hands off anything already tracked. Never commit.
