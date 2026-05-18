# Vitest Test Runner Agent

This agent runs the Vitest test suite and reports results.

## How to Use

Invoke this agent with:
```
/path/to/claude agent test-agent
```

Or if configured as a skill:
```
/test-agent
```

## Function

When invoked, this agent:
1. Runs `npm test` (which executes `vitest`)
2. Reports any test failures or errors
3. Provides a summary of test results including passed/failed counts
4. Can run specific test files if arguments are provided

## Implementation Notes

- Requires npm and vitest to be available in the path
- Uses the test script defined in package.json
- Supports passing specific test file patterns as arguments
- Returns exit code 0 if all tests pass, non-zero if failures occur