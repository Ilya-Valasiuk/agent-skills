# Pull Request Reference

## Contents

- Base branch rules
- Classifying Features vs Fixes
- Writing PR bullets
- Writing PR titles
- Tooling guidance

## Base branch rules

- Default target branch: `develop`
- Use another target when the user explicitly requests it or the repo flow clearly requires it
- For release PRs to `main`, always use the title `Release`

## Classifying Features vs Fixes

Use actual behavior change, not file names.

### Features

Put an item in `Features` when the branch:

- introduces a new user-facing or developer-facing capability
- adds a new flow, page, API integration, or behavior
- meaningfully expands an existing workflow

### Fixes

Put an item in `Fixes` when the branch:

- corrects broken behavior
- resolves an error, regression, or edge case
- improves incorrect output or interaction without adding a new capability

### Neutral changes

If a change is mostly refactor, cleanup, tests, or maintenance, do not force it into either section unless it materially helps reviewer understanding.

If no real items exist for a section, use `N/A`.

## Writing PR bullets

Prefer one concise line per item.

If a work item link is known:

```md
- [Feature or fix name](https://dev.azure.com/link-to-the-work-item)
```

If a link is known and a short explanation adds value:

```md
- [Feature or fix name](https://dev.azure.com/link-to-the-work-item): short description
```

If no link is known:

```md
- Name: short clear description
```

Avoid vague bullets like:

- `Updated code`
- `Bug fixes`
- `Improvements`

## Writing PR titles

Title priority:

1. task or work item name when it clearly matches the branch
2. branch purpose inferred from diff and commits
3. concise synthesized title

Guidelines:

- keep it short
- focus on the main outcome
- prefer natural language over commit prefixes unless the repo clearly expects them
- avoid combining unrelated changes into one title

Examples:

- `Add filtering to project list`
- `Fix duplicate submission in contact form`
- `Implement blog article search`

Special case:

- release PR to `main` -> `Release`

## Tooling guidance

Useful commands:

```bash
git branch --show-current
git status --short
git log --oneline --decorate -n 15
git diff --stat origin/develop...HEAD
git diff origin/develop...HEAD
```

Git cannot create pull requests by itself. It can only push branches.

To create a PR automatically, use repo-host tooling such as:

```bash
gh pr create --title "<title>" --body-file <temp-file>
```

If that tooling is unavailable, fall back to the compare-link handoff.
