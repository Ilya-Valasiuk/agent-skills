# Component validation checklist

Run this checklist after creating or updating a component.

## Structure checks

- [ ] Component is in the correct directory (`common` vs page-specific)
- [ ] Folder names are kebab-case
- [ ] File name is PascalCase
- [ ] One component per file
- [ ] Sub-components are under a `components/` folder when needed

## Implementation checks

- [ ] Component uses named export (no default export)
- [ ] Export uses `React.FC<Props>` (or `React.FC` without props)
- [ ] `Props` type exists when props are used
- [ ] Props order is: required, optional, function props
- [ ] Exported component name matches file name
- [ ] Simple JSX-only component uses implicit return

## Integration checks

- [ ] Imports resolve without path errors
- [ ] No obvious dead code introduced
- [ ] Linter/type checker reports no new issues in edited files

## Verification loop

If any item fails:
1. Fix the issue
2. Re-check all failed items
3. Repeat until all required items pass
