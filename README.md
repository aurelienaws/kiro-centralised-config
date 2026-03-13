# Kiro Team Conventions

Central repository for our team's [Kiro](https://kiro.dev) steering files and skills. This is the single source of truth for how our AI coding assistant behaves across all projects.

## What's in here

- Steering files define coding standards, patterns, and rules that Kiro follows
- Skills are reusable instructions for specific tasks (code reviews, testing patterns, etc.)

## Repo structure

```
├── steering/                          # Shared — applies to all projects
│   └── a-global-steering.md
├── skills/                            # Shared — applies to all projects
│   ├── a-global-skill/
│   │   └── SKILL.md
│   └── another-global-skill/
│       └── SKILL.md
├── python/                            # Python-specific conventions
│   ├── steering/
│   │   └── a-python-steering.md
│   └── skills/
│       ├── a-python-skill/
│       │   └── SKILL.md
│       └── another-python-skill/
│           └── SKILL.md
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

- `steering/` and `skills/` at the root are shared conventions that apply to every project regardless of language or framework
- Named folders (`python/`, `typescript/`) contain type-specific conventions that are layered on top for projects that need them

This way, team-wide standards are defined once and language-specific guidance is added where it matters.

## Adding a new type

Create a folder at the root with `steering/` and/or `skills/` inside:

```
cdk/
  steering/
    construct-patterns.md
  skills/
    cdk-deploy-helper/
      SKILL.md
```

## Updating conventions

Open a PR. Review as a team. Once merged, it becomes the new standard.
