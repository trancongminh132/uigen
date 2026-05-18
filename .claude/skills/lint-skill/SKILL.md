---
name: lint-skill
description: Runs ESLint linting on the codebase to check for code quality and formatting issues
---

# Linting Skill

This skill runs ESLint linting on the entire codebase to identify code quality, formatting, and potential errors.

## How to Use

Invoke this skill with:
```
/lint-skill
```

Or if you prefer to describe what you want:
"Run ESLint linting on the codebase"

## Function

When invoked, this skill:
1. Runs `npm run lint` (which executes `next lint`)
2. Reports any linting errors or warnings
3. Provides a summary of the linting status
4. Returns exit code 0 if linting passes, non-zero if issues found

## Implementation

This skill executes the following command:
```bash
npm run lint
```

Which runs:
```bash
next lint
```

## Expected Output

- **Success**: "ESLint check completed successfully. No warnings or errors were found in the codebase."
- **Failure**: Detailed linting error messages with file paths, line numbers, and rule violations

## Example Usage

```
/lint-skill
```

Output when successful:
```
ESLint check completed successfully. No warnings or errors were found in the codebase.
```

Output when issues found:
```
> uigen@0.1.0 lint
> next lint

✖ ESLint: Failed to compile.

src/components/example.tsx
  10:5  error  Missing React import  react/react-in-jsx-scope
  15:20 error  'unusedVar' is defined but never used  @typescript-eslint/no-unused-vars

✖ 2 problems (2 errors, 0 warnings)
```

## Integration with Workflow

This skill is designed to be used as part of the code review workflow. When used in the workflow-skill:
- If linting passes, workflow continues to testing
- If linting fails, workflow stops and reports the error