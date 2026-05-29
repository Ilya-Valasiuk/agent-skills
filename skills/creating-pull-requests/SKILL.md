---
name: creating-pull-requests
description: Prepare and open pull requests using the team's PR template, including a short PR title, diff-based classification into Features and Fixes, and an approval checkpoint before any push or PR creation. Use when the user asks to create, draft, preview, or open a pull request.
license: MIT
allowed-tools: Bash
---

# Creating Pull Requests

Prepare a PR from the current branch, show a preview, and open it only after explicit approval.

## Rules

- Inspect the real branch changes before drafting the PR.
- Always show the title and body preview before pushing or opening the PR.
- Never push or create a PR without explicit approval.
- If `Features` or `Fixes` has no real items, write `N/A`.
- For release PRs targeting `main`, always use the title `Release`.

## Workflow

Copy this checklist and track progress:

```text
PR Progress:
- [ ] Step 1: Inspect branch and choose base
- [ ] Step 2: Identify main story and work items
- [ ] Step 3: Classify items into Features and Fixes
- [ ] Step 4: Draft title and PR body
- [ ] Step 5: Show preview and wait for approval
- [ ] Step 6: Push and open PR, or provide fallback handoff
```

### Step 1: Inspect branch and choose base

Check branch name, status, commits, and diff against the target branch.

Default base: `origin/develop`

Use another base when:

- the user explicitly names it
- the repo flow clearly uses another target
- this is a release PR to `main`

If the correct base is unclear, ask before finalizing.

Common commands:

```bash
git branch --show-current
git status --short
git log --oneline --decorate -n 15
git diff --stat origin/develop...HEAD
git diff origin/develop...HEAD
```

### Step 2: Identify the branch story

Summarize what the branch mainly does.

Prefer task names and work item links from:

- user context
- branch names
- commit messages
- issue or board references

### Step 3: Classify items

Use behavior, not filenames.

- `Features`: new or expanded capability
- `Fixes`: corrected broken behavior, regression, or edge case

Do not force refactors or maintenance work into either section unless they are the only changes worth mentioning for reviewer context.

Classification and bullet patterns: see [references/REFERENCE.md](references/REFERENCE.md)

### Step 4: Draft title and body

Title priority:

1. task or work item name, if it clearly matches the branch
2. main outcome inferred from the diff
3. concise synthesized title

Prefer short natural-language titles focused on the main outcome.

Build the PR body using the exact team template from [references/TEMPLATES.md](references/TEMPLATES.md).

### Step 5: Show preview and wait

Before any push or PR creation, show:

- proposed PR title
- proposed PR body
- target base branch when useful

Use the preview template from [references/TEMPLATES.md](references/TEMPLATES.md), then stop and wait for approval.

### Step 6: Push and open PR, or provide fallback handoff

After approval:

- push the branch if needed
- create the PR with the approved title and body

If GitHub CLI is available, prefer `gh pr create`.

If PR creation succeeds, use the success response template from [references/TEMPLATES.md](references/TEMPLATES.md).

If automatic PR creation is blocked because of missing CLI, invalid auth, sandbox/network restrictions, or unavailable repo tooling, do not stop with an error. Use the fallback response template from [references/TEMPLATES.md](references/TEMPLATES.md) and provide a complete manual handoff.

For GitHub compare links, use:

```text
https://github.com/<owner>/<repo>/compare/<base>...<head>?expand=1
```

## References

- [references/REFERENCE.md](references/REFERENCE.md): classification rules, title guidance, command guidance
- [references/TEMPLATES.md](references/TEMPLATES.md): team PR body template, preview template, success template, fallback template
- [references/EXAMPLES.md](references/EXAMPLES.md): example scenarios
