# Kiro Team Conventions

Central repository for our team's Kiro steering files, skills, agents, and hooks. This is the single source of truth for how our AI coding assistant behaves across all projects.

## What's in here

- **Steering files** define coding standards, patterns, and rules that Kiro follows
- **Skills** are reusable instructions for specific tasks (code reviews, testing patterns, etc.)
- **Agents** are custom agent definitions that extend Kiro with specialized capabilities
- **Hooks** are automation triggers that run commands or inject prompts on specific events

## Repo structure

```
├── steering/                          # Shared — applies to all projects
│   └── a-global-steering.md
├── skills/                            # Shared — applies to all projects
│   ├── a-global-skill/
│   │   └── SKILL.md
│   └── another-global-skill/
│       └── SKILL.md
├── agents/                            # Shared — applies to all projects
│   └── global-agent.md
├── hooks/                             # Shared — applies to all projects (shared-only)
│   └── lint-on-save.json
├── python/                            # Python-specific conventions
│   ├── steering/
│   │   └── a-python-steering.md
│   ├── skills/
│   │   ├── a-python-skill/
│   │   │   └── SKILL.md
│   │   └── another-python-skill/
│   │       └── SKILL.md
│   └── agents/
│       └── python-agent.md
└── typescript/                        # TypeScript-specific conventions
    ├── steering/
    │   └── a-ts-steering.md
    └── skills/
        ├── a-typescript-skill/
        │   └── SKILL.md
        └── another-ts-skills/
            └── SKILL.md
```

## How it's organized

Conventions are split into two layers:

- `steering/`, `skills/`, `agents/`, and `hooks/` at the root are **shared conventions** that apply to every project regardless of language or framework
- Named folders (`python/`, `typescript/`) contain **type-specific conventions** that are layered on top for projects that need them

**Note:** Hooks are shared-only. They are not synced from type-specific directories since they are project-level automation.

Skills and agents sync all file types (not just `.md`), so you can include supporting files like images, YAML configs, or reference docs alongside them.

## Adding a new type

Create a folder at the root with `steering/`, `skills/`, and/or `agents/` inside:

```
cdk/
  steering/
    construct-patterns.md
  skills/
    cdk-deploy-helper/
      SKILL.md
  agents/
    cdk-agent.md
```

## Adding hooks

Hooks live only at the root level in `hooks/`. They support two formats:

- `.kiro.hook` — legacy hook format
- `.json` — new v1 hook format

```json
{
  "version": "v1",
  "hooks": [{
    "name": "Lint on Save",
    "trigger": "PostFileSave",
    "matcher": "\\.(ts|js)$",
    "action": { "type": "command", "command": "npm run lint" }
  }]
}
```

## Updating conventions

Open a PR. Review as a team. Once merged, it becomes the new standard.
