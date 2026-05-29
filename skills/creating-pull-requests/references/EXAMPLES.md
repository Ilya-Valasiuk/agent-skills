# Pull Request Examples

## Example 1: Standard branch PR

Input: `Create a PR for this branch.`

Expected behavior:

- inspect the branch and diff
- infer the main branch outcome
- classify changes into `Features` and `Fixes`
- draft title and body
- show preview and wait for approval

## Example 2: Task-linked PR

Input: `Open PR for task ABC-123.`

Expected behavior:

- reuse task name and link if available
- write linked bullets in the correct section
- show preview and wait for approval

## Example 3: Release PR

Input: `Create release PR to main.`

Expected behavior:

- target `main`
- always use the title `Release`
- still analyze the diff to populate `Features` and `Fixes`
- wait for approval before pushing or opening the PR

## Example 4: Tooling blocked

Input: `Create the PR, but the CLI is unavailable.`

Expected behavior:

- prepare the approved title and body
- build the compare link
- return the manual fallback response with title, body, base branch, head branch, and compare link
