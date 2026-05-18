# ESLint Linting Agent

This agent runs ESLint linting on the codebase and reports results.

## How to Use

Invoke this agent with:
```
/path/to/claude agent lint-agent
```

Or if configured as a skill:
```
/lint-agent
```

## Function

When invoked, this agent:
1. Runs `npm run lint` (which executes `next lint`)
2. Reports any linting errors or warnings
3. Provides a summary of the linting status

## Implementation Notes

- Requires npm and next.js to be available in the path
- Uses the lint script defined in package.json
- Returns exit code 0 if linting passes, non-zero if issues found