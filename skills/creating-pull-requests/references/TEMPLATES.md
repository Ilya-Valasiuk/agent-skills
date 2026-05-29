# Pull Request Templates

## Team PR body template

Use this exact body structure:

```md
# Features

<!-- please provide a list of the new features introduced in this pull request with links to the related work items -->

- [feature 1](https://dev.azure.com/link-to-the-work-item)
- [feature 2](https://dev.azure.com/link-to-the-work-item)

# Fixes

<!-- please provide a list of the fixes made in this pull request with links to the related work items -->

- [fix 1](https://dev.azure.com/link-to-the-work-item)
- [fix 2](https://dev.azure.com/link-to-the-work-item)

## Checklist before requesting a review

- [ ] I have tested changes locally;
- [ ] I have followed styleguide;
- [ ] I have performed a self-review of my code.
```

Adaptation rules:

- replace placeholder bullets with real items
- if there are no feature items, write `N/A` under `# Features`
- if there are no fix items, write `N/A` under `# Fixes`
- keep the checklist untouched unless the user explicitly asks to mark items

## Preview template

Before approval, show:

```md
Proposed PR title:
<title>

Proposed PR body:
<body>
```

## Success template

If the PR is created successfully, respond with:

```md
The PR is created: #<number>

Title: <title>
Link: [<owner>/<repo>#<number>](<pr-url>)
Base branch: <base>
Head branch: <head>
```

## Fallback template

If automatic PR creation is blocked, respond with:

```md
I couldn't create the PR automatically, so here is everything needed to open it manually.

Title: <title>
Base branch: <base>
Head branch: <head>
Compare link: <compare-url>

Body:
<full-pr-body>
```
