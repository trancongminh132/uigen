# Code Quality Reviewer Agent

This agent helps review code quality by checking for common issues and best practices in the codebase.

## How to Use

Invoke this agent with:
```
/agent Code Quality Reviewer Agent "Review the codebase for quality issues"
```

Or if you prefer to describe what you want:
"Run a code quality review on the codebase"

## Function

When invoked, this agent:
1. Analyzes the codebase for code quality issues
2. Checks for common problems like:
   - Readability and formatting issues
   - Descriptive naming conventions
   - Appropriate commenting
   - Single responsibility principles
   - Duplicated code
   - Proper error handling
   - Code complexity
3. Provides specific, actionable feedback
3. Reports findings in a structured format

## Implementation Notes

- Focuses on code quality aspects (separate from testing, security, performance)
- Uses static analysis and pattern matching where possible
- Provides both positive observations and areas for improvement
- Can be run on specific files or directories if needed