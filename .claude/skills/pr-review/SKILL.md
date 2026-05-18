---
name: pr-review
description: Helps you review pull requests systematically by checking for common issues and best practices.
---

# PR Review Skill

This skill helps you review pull requests systematically by checking for common issues and best practices.

## How to Use

When reviewing a PR, follow these steps:

1. **Understand the Context**: Read the PR description and related issues/tickets
2. **Check Code Changes**: Review the actual code modifications
3. **Run Through Checklist**: Use the checklist below to identify potential issues
4. **Provide Feedback**: Give clear, actionable feedback to the author

## Review Checklist

### Code Quality
- [ ] Is the code readable and well-formatted?
- [ ] Are variable and function names descriptive?
- [ ] Is there appropriate commenting where needed?
- [ ] Are functions/hooks focused on a single responsibility?
- [ ] Is there any duplicated code that could be extracted?

### Architecture & Design
- [ ] Do the changes follow the existing codebase patterns?
- [ ] Are components properly encapsulated?
- [ ] Is state management appropriate?
- [ ] Are props/types properly defined and used?
- [ ] Are imports organized correctly?

### Testing
- [ ] Are new features accompanied by tests?
- [ ] Do existing tests still pass?
- [ ] Are edge cases considered in tests?
- [ ] Is test coverage adequate for the changes?

### Performance
- [ ] Are there any potential performance bottlenecks?
- [ ] Are expensive operations memoized where appropriate?
- [ ] Are lists/collections properly keyed?
- [ ] Are there any unnecessary re-renders possible?

### Security
- [ ] Is user input properly validated/sanitized?
- [ ] Are there any potential injection vulnerabilities?
- [ ] Are secrets/tokens handled correctly (not hardcoded)?
- [ ] Are authentication/authorization checks in place where needed?

### Accessibility (a11y)
- [ ] Are interactive elements accessible via keyboard?
- [ ] Are ARIA attributes used appropriately?
- [ ] Is color contrast sufficient?
- [ ] Are form elements properly labeled?

### Style & Consistency
- [ ] Does the code follow the project's style guide?
- [ ] Are Tailwind classes used consistently?
- [ ] Are component names and file names consistent?
- [ ] Are imports using the '@/ ' alias correctly?

### Documentation
- [ ] Is the PR description clear and complete?
- [ ] Are complex algorithms or decisions explained?
- [ ] Is documentation updated if needed?
- [ ] Are JSDoc comments added for complex functions?

## Common Issues to Look For

### React-Specific
- Missing dependency arrays in useEffect/useCallback
- Direct state mutations instead of using setState
- Using index as key in lists when items can be reordered/deleted
- Not cleaning up subscriptions/timers in useEffect
- Creating new objects/arrays in render causing unnecessary re-renders

### TypeScript-Specific
- Using `any` type when more specific types could be used
- Not handling nullable/undefined cases
- Missing return types on functions
- Overly complex type definitions that could be simplified

### Next.js-Specific
- Missing proper metadata/SEO in pages
- Not using next/image for images
- Incorrect usage of getStaticProps/getServerSideProps
- Not handling loading/error states in data fetching

## Providing Feedback

When giving feedback:
1. Be specific about what needs to be changed
2. Explain why the change is important
3. Suggest concrete alternatives when possible
4. Balance criticism with positive observations
5. Use a respectful and collaborative tone

Example formats:
- "Consider renaming `x` to `y` for better clarity because..."
- "This might cause a performance issue because... Try doing ... instead."
- "Great job on handling the edge case here!"
- "Have you considered using ... instead? It would make the code more ..."