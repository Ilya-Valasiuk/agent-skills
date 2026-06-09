# Agent Skills

A collection of reusable Agent Skills for Cursor to standardize and accelerate AI-assisted development workflows.

## What are Agent Skills?

Agent Skills are instructions that teach Cursor's AI agent how to perform specific, repeatable tasks according to your project conventions. When a skill is referenced, the agent reads its instructions and follows a defined workflow — ensuring consistent output every time.


## Repository Structure

```
skills/
└── [skill-name]/
    ├── SKILL.md              # Required: skill definition with frontmatter and instructions
    ├── references/           # Optional: supporting documentation files
    ├── scripts/              # Optional: executable code/utilities
    └── assets/               # Optional: templates, images, data files
```

## SKILL.md Format

Every skill must contain a `SKILL.md` file with YAML frontmatter and Markdown body.

### Required Frontmatter

```yaml
---
name: skill-name
description: A description of what this skill does and when to use it.
---
```

### Frontmatter Fields

| Field | Required | Constraints |
|-------|----------|-------------|
| `name` | Yes | Max 64 chars. Lowercase, numbers, hyphens only. No leading/trailing hyphens. Must match parent directory name. |
| `description` | Yes | Max 1024 chars. Should describe WHAT it does and WHEN to use it. |
| `license` | No | License name or reference (e.g., "MIT", "Apache-2.0") |
| `compatibility` | No | Environment requirements, system packages, network access needs. |
| `metadata` | No | Arbitrary key-value pairs for additional context. |
| `allowed-tools` | No | Space-delimited list of pre-approved tools. (Experimental) |

### Body Content

The Markdown body after frontmatter contains the skill instructions. Recommended sections:

- Step-by-step instructions
- Workflow examples
- Validation checklist
- Edge cases and considerations

**Context Efficiency:** Keep `SKILL.md` under 500 lines. Move detailed reference material to separate files in `references/`.

## Optional Directories

### `references/`
Supporting documentation loaded on-demand by agents:
- `REFERENCE.md` - Technical reference
- `FORMS.md` - Form templates or structured data formats
- Domain-specific files (`finance.md`, `legal.md`, etc.)

### `scripts/`
Executable code agents can run:
- Python, Bash, JavaScript, etc.
- Must be self-contained or clearly document dependencies
- Include helpful error messages

### `assets/`
Static resources:
- Document templates, configuration templates
- Diagrams, images, examples
- Lookup tables, schemas

## Available Skills

Install pattern:

```bash
npx skills add https://github.com/ilya-valasiuk/agent-skills --skill <skill-name>
```

| Skill | Description | Install |
|---|---|---|
| [building-components](skills/building-components/SKILL.md) | Builds, restructures, and standardizes React components according to project conventions (placement, folder/file naming, exports, props patterns). | `npx skills add https://github.com/ilya-valasiuk/agent-skills --skill building-components` |
| [creating-pull-requests](skills/creating-pull-requests/SKILL.md) | Prepare and open pull requests using the team's PR template, including a short PR title, diff-based classification into Features and Fixes, and an approval checkpoint before any push or PR creation. | `npx skills add https://github.com/ilya-valasiuk/agent-skills --skill creating-pull-requests` |
| [generating-typeorm-migration](skills/generating-typeorm-migration/SKILL.md) | Explains how to create and review TypeORM migrations. Use this skill whenever the user wants to change an entity, add or update schema-related database objects, generate a migration, or decide whether a database change should be handled through TypeORM metadata or a custom migration. | `npx skills add https://github.com/ilya-valasiuk/agent-skills --skill generating-typeorm-migration` |
| [organizing-classnames](skills/organizing-classnames/SKILL.md) | Enforces classNames package usage patterns and Tailwind CSS class ordering conventions in React components. Use this skill whenever writing or reviewing component className props, applying Tailwind classes, using the classnames package, organizing breakpoint-specific styles, writing conditional class expressions, or when the user asks about CSS class ordering, mobile-first responsive patterns, or how to handle className props in components. | `npx skills add https://github.com/ilya-valasiuk/agent-skills --skill organizing-classnames` |

## Experimental Skills

These skills are experimental and are not recommended for production use.

- [structuring-nextjs-app-router](skills/structuring-nextjs-app-router/SKILL.md)
  Standardizes Next.js App Router project structure across `src/`, including route files, page composition, API modules, server actions, hooks, providers, helpers, and shared utilities.
  Install: `npx skills add https://github.com/ilya-valasiuk/agent-skills --skill structuring-nextjs-app-router`


## Resources & Documentation

- [Agent Skills Specification](https://agentskills.io/llms.txt) - Official format specification
- [Cursor Skills Documentation](https://cursor.com/docs/context/skills) - Cursor-specific implementation guide
- [Agent Skills Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) - Authoring guidelines and patterns

## License

MIT License - see [LICENSE](LICENSE) file for details.
