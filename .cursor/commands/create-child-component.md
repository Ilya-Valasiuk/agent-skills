# Create Child Component

## Overview
Extract selected code into a new child component following project conventions and best practices.

## Steps

1. **Analyze the selected code**
- [ ] Identify what the code does and what props it needs
- [ ] Determine an appropriate component name based on its purpose
- [ ] Identify any dependencies (imports, hooks, etc.)

2. **Create the new component**
- [ ] Follow component structure from `.cursor/rules/component-structure.mdc`
- [ ] Apply className conventions from `.cursor/rules/classnames-conventions.mdc`
- [ ] Use named exports with arrow function syntax
- [ ] Define proper TypeScript types for props

3. **Update parent component**
- [ ] Replace selected code with new component usage
- [ ] Add import statement for the new component
- [ ] Pass all necessary props with proper types matching child component's prop definitions
- [ ] Handle type mismatches: make props optional, provide fallbacks, or add type guards

## Component Creation Checklist
- [ ] Component folder structure created according to rules
- [ ] Component name is descriptive and follows conventions
- [ ] Component uses named export with arrow function
- [ ] Props are properly typed with `type Props`
- [ ] className conventions followed
- [ ] All necessary imports included in child component
- [ ] Parent component updated with import and usage
- [ ] Props passed from parent match child component's type definitions
- [ ] Type compatibility verified (no undefined/null issues)
- [ ] No TypeScript errors in parent or child
