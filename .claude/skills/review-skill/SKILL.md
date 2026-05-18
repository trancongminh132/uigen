---
name: review-skill
description: Runs a code quality review on the codebase to check for readability, best practices, and potential improvements
---

# Code Review Skill

This skill runs a comprehensive code quality review on the codebase to identify readability issues, best practice violations, and areas for improvement.

## How to Use

Invoke this skill with:
```
/review-skill
```

Or if you prefer to describe what you want:
"Run a code quality review on the codebase"

## Function

When invoked, this skill:
1. Analyzes the codebase for code quality issues using patterns and heuristics
2. Checks for common problems like:
   - Readability and formatting issues
   - Descriptive naming conventions
   - Appropriate commenting and documentation
   - Single responsibility principles
   - Duplicated code
   - Proper error handling
   - Code complexity
   - Performance anti-patterns
3. Provides specific, actionable feedback with both positive observations and areas for improvement
4. Returns a structured review report

## Implementation

This skill uses Claude Code's agent system to run a code quality review similar to the code-quality-reviewer agent. It examines:
- TypeScript/JavaScript files for code quality
- React components for best practices
- Configuration files for consistency
- Overall project structure and patterns

## Expected Output

The skill returns a detailed review report with sections:
- **✅ Positive Observations**: What's working well in the codebase
- **⚠️ Areas for Improvement**: Specific issues found with recommendations
- **🔧 Specific Refactoring Examples**: Concrete code examples of how to fix issues
- **📊 Summary**: Overall assessment of code health

## Example Usage

```
/review-skill
```

Sample output (truncated for brevity):
```
## Code Quality Review: UIGen Codebase

After reviewing the codebase, here are my observations regarding code quality, formatting, naming conventions, and potential improvements:

### ✅ **Positive Observations**
1. **Clean Architecture**: Clear separation of concerns...
2. **Modern Tech Stack**: Proper use of Next.js 15 App Router...
3. **Consistent TypeScript Usage**: Strong typing throughout...

### ⚠️ **Areas for Improvement**
#### 1. **Inconsistent Naming Conventions**
- **Issue**: Mixed naming patterns in `src/lib/provider.ts`...
- **Recommendation**: Standardize on verb-noun naming...

#### 2. **Magic Numbers and Hardcoded Values**
- **Issue**: Hardcoded delay values (25ms, 15ms, 30ms) and token counts...
- **Recommendation**: Extract to named constants at file top...

### 🔧 **Specific Refactoring Examples**
**For the MockLanguageModel (`src/lib/provider.ts`):**
Instead of large switch statements, consider using configuration objects...

### 📊 **Summary**
**Strengths**: Solid architectural foundation...
**Opportunities**: Improve consistency in naming, reduce code duplication...
```

## Integration with Workflow

This skill is designed to be used as part of the code review workflow. When used in the workflow-skill:
- If review passes (no critical issues found), workflow considers it successful
- If review finds significant issues, workflow reports them but typically doesn't block (as code quality is often advisory rather than blocking)
- The workflow will show the review results for user consideration