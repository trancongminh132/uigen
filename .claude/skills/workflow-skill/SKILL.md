---
name: workflow-skill
description: Runs a complete code review workflow including linting, testing, and code quality checks
---

# Code Review Workflow Skill

This skill runs a complete automated workflow that performs linting, testing, and code quality review in sequence, stopping if any check fails.

## How to Use

Invoke this skill with:
```
/workflow-skill
```

Or if you prefer to describe what you want:
"Run the complete code review workflow on the codebase"

## Function

When invoked, this skill runs the following checks in sequence:
1. **Linting Check** (`/lint-skill`) - Runs ESLint to check for code quality and formatting issues
2. **Testing Check** (`/test-skill`) - Runs Vitest to ensure all tests pass  
3. **Code Quality Review** (`/review-skill`) - Performs comprehensive code quality analysis

The workflow stops at the first failed check and reports the error. If all checks pass, it reports success.

## Implementation

This skill orchestrates the execution of three other skills:
- `/lint-skill` - For ESLint linting
- `/test-skill` - For Vitest testing  
- `/review-skill` - For code quality review

Each skill is invoked sequentially, and the workflow proceeds only if the previous skill succeeds.

## Expected Output

The skill provides clear output showing:
- Which check is currently running
- Results of each check (pass/fail)
- Overall workflow status (success or failure with reason)
- Next steps guidance

## Example Usage

```
/workflow-skill
```

### Successful Workflow Output:
```
🔍 Starting code review workflow...

📝 Step 1/3: Running linting check...
ESLint check completed successfully. No warnings or errors were found in the codebase.
✅ Linting check passed!

🧪 Step 2/3: Running testing check...
All tests passed successfully! 

**Test Results Summary:**
- **Test Files:** 9 passed
- **Total Tests:** 185 passed
- **Duration:** 4.57 seconds
✅ Testing check passed!

🔎 Step 3/3: Running code quality review...
[Code quality review output would appear here]
✅ Code quality review completed!

🎉 All checks passed! The codebase is ready for committing.
Next steps: Use /commit-skill to help generate a proper commit message, then commit your changes.
```

### Failed Workflow Output (Example - Linting Failure):
```
🔍 Starting code review workflow...

📝 Step 1/3: Running linting check...
> uigen@0.1.0 lint
> next lint

✖ ESLint: Failed to compile.

src/components/example.tsx
  10:5  error  Missing React import  react/react-in-jsx-scope
  15:20 error  'unusedVar' is defined but never used  @typescript-eslint/no-unused-vars

✖ 2 problems (2 errors, 0 warnings)
❌ Linting check failed!

🛑 Workflow stopped due to linting failure.
Please fix the linting errors above and run the workflow again.
```

## Integration with Other Skills

This workflow skill is designed to work with:
- **/commit-skill** - For generating properly formatted commit messages after workflow passes
- **/lint-skill**, **/test-skill**, **/review-skill** - Individual check skills that can be run separately
- **Existing agents** - Reuses the logic from lint-agent, test-agent, and code-quality-reviewer agents

## Customization

Users can also run individual checks if they prefer:
- `/lint-skill` - Just run linting
- `/test-skill` - Just run testing  
- `/review-skill` - Just run code quality review
- `/workflow-skill` - Run all checks in sequence (recommended for pre-commit validation)

## Best Practices

1. **Run workflow before committing** - Ensures code quality is maintained
2. **Fix issues in order** - Address linting first, then testing, then code quality concerns
3. **Use commit-skill after workflow passes** - Helps generate properly formatted commit messages
4. **Consider running workflow periodically** - Even when not committing, to maintain code health