---
name: test-skill
description: Runs the Vitest test suite on the codebase to ensure all tests pass
---

# Testing Skill

This skill runs the Vitest test suite on the entire codebase to verify that all tests pass.

## How to Use

Invoke this skill with:
```
/test-skill
```

Or if you prefer to describe what you want:
"Run the Vitest test suite on the codebase"

## Function

When invoked, this skill:
1. Runs `npm test` (which executes `vitest`)
2. Reports any test failures or errors
3. Provides a summary of test results including passed/failed counts
4. Returns exit code 0 if all tests pass, non-zero if failures occur

## Implementation

This skill executes the following command:
```bash
npm test
```

Which runs:
```bash
vitest
```

## Expected Output

- **Success**: Message indicating all tests passed, including number of test files and total tests, and duration.
- **Failure**: Detailed test error messages with stack traces and failing test descriptions.

## Example Usage

```
/test-skill
```

Output when successful:
```
All tests passed successfully! 

**Test Results Summary:**
- **Test Files:** 9 passed
- **Total Tests:** 185 passed
- **Duration:** 4.57 seconds
```

Output when failures occur:
```
> uigen@0.1.0 test
> vitest

  ❌ src/components/example.test.tsx:5:2
    expect(received).toBe(expected) // Object.is equality

    Expected: 5
    Received: 3

    ❌ 1 failed, 0 passed, 1 total (1 test file)
```

## Integration with Workflow

This skill is designed to be used as part of the code review workflow. When used in the workflow-skill:
- If testing passes, workflow continues to code quality review
- If testing fails, workflow stops and reports the error