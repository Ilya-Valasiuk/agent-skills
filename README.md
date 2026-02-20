# Agent Skills

A collection of reusable Agent Skills for Cursor to standardize and accelerate AI-assisted development workflows.

## What are Agent Skills?

Agent Skills are instructions that teach Cursor's AI agent how to perform specific, repeatable tasks according to your project conventions. When a skill is referenced, the agent reads its instructions and follows a defined workflow — ensuring consistent output every time.

See the [Cursor Skills Documentation](https://cursor.com/docs/context/skills) for more details.

## Repository Structure

```
skills/
└── [skill-name]/
    ├── SKILL.md          # Skill entry point with workflow and validation 
    └── references/       # Supporting reference files linked from SKILL.md
        └── *.md
```

## Available Skills

| Skill | Description |
|---|---|
| [building-components](skills/building-components/SKILL.md) | Builds, restructures, and standardizes React components according to project conventions (placement, folder/file naming, exports, props patterns). |


```

## License

MIT License - see [LICENSE](LICENSE) file for details.
