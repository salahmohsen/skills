# aha-quests

Learn a skill by building real features in your own project. The agent proposes mini-projects ("quests"), writes a task vault, and mentors you through it — without ever handing you the answer.

## Install

```
npx skills add salahmohsen/skills
```

Or symlink for local use:

```bash
git clone <repo> ~/Developer/skills
ln -s ~/Developer/skills/aha-quests ~/.claude/skills/aha-quests
ln -s ~/Developer/skills/aha-quests ~/.agents/skills/aha-quests
```

## Use

Say any of:

- "I want to learn better-auth"
- "teach me Prisma migrations"
- "prep me for this role" + paste a job description

The agent reads your repo, proposes three quests, and builds an `aha/` vault you can open in Obsidian.

## How it works

- **Coupling rule** — every quest forces the thing you're learning to work with 2+ pieces of your real stack. Integration is the lesson.
- **Per-step sizing** — before each step the agent asks `micro` / `step` / `slice`, because difficulty varies. Easy steps stay whole; hard ones get split.
- **Action-first output** — every reply leads with the next action; no preamble or recap.
- **Hint ladder** — when stuck, the agent narrows, points, analogizes, then explains. Never gives code.
- **Flow guard** — stuck ~15 min? A hint drops automatically. No spinning.
- **Code is truth** — on resume the agent reads your repo, not its own notes.

## Files

```
aha-quests/
├── SKILL.md
└── references/
    ├── quest-design.md
    ├── vault-format.md
    └── mentor-ladder.md
```

## License

MIT
