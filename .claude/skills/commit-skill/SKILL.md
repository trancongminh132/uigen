---
name: commit-skill
description: Helps generate properly formatted commit messages following the project's "Test App: " prefix convention
---

# Commit Message Skill

This skill helps users generate properly formatted commit messages that follow the project's convention of using the "Test App: " prefix and conventional commit format.

## How to Use

Invoke this skill with:
```
/commit-skill
```

Or if you prefer to describe what you want:
"Help me generate a proper commit message"
"Show me how to format my commit message"

## Function

When invoked, this skill:
1. Explains the project's commit message format requirements
2. Provides interactive prompts (via guidance) for commit type, scope, and description
3. Validates the format: `Test App: <type>(<scope>): <description>`
4. Generates a properly formatted commit message based on user input
5. Provides examples of valid commit messages for different scenarios
6. Explains when to use each commit type

## Commit Message Format

All commit messages in this project must follow this format:
```
Test App: <type>(<scope>): <description>
```

### Elements:
- **Test App: ** - Required prefix for all commits in this project
- **<type>** - The type of change (feat, fix, docs, style, refactor, test, chore, etc.)
- **<scope>** - Optional: the part of the codebase affected (component, api, ui, etc.)
- **<description>** - Brief summary of the change (imperative mood, max 50 chars)

### Types:
- **feat**: A new feature
- **fix**: A bug fix
- **docs**: Documentation changes
- **style**: Formatting, missing semi-colons, etc. (no code change)
- **refactor**: Code refactoring (neither fixes bug nor adds feature)
- **test**: Adding or modifying tests
- **chore**: Build process or auxiliary tool changes
- **perf**: Performance improvements
- **ci**: CI/CD related changes
- **build**: Changes that affect the build system

## Implementation

This skill provides guidance and validation for creating commit messages. It does not directly execute git commands but helps users prepare properly formatted messages that they can then use with standard git commit commands.

## Interactive Guidance

When using this skill, consider:

1. **Choose your type**: What kind of change are you making?
2. **Choose your scope (optional)**: What part of the codebase is affected?
3. **Write your description**: What did you change? (Use imperative mood)

## Example Usage

```
/commit-skill
```

The skill will guide you through the process with examples and validation.

### Example Interactive Flow:
```
Skill: Commit Message Helper

What type of change is this? (feat, fix, docs, style, refactor, test, chore, perf, ci, build)
> feat

What is the scope of this change? (optional, e.g., component, api, ui) 
> ui

What is your description? (imperative mood, max 50 chars, no period)
> add responsive navigation menu with dropdown

Generated commit message:
Test App: feat(ui): add responsive navigation menu with dropdown
```

## Examples of Valid Commit Messages

- `Test App: feat(ui): add card component with title and action button`
- `Test App: fix(auth): resolve sign-in form validation error`
- `Test App: docs: update README with setup instructions`
- `Test App: style: format components according to eslint rules`
- `Test App: refactor(api): extract user service to separate module`
- `Test App: test: add unit tests for badge component`
- `Test App: chore: update dependencies to latest versions`
- `Test App: perf: optimize image loading in product gallery`
- `Test App: ci: add github Actions workflow for automated testing`

## Commit Body (Optional)

For complex changes, you can add a body after a blank line:
```
Test App: feat(api): add user authentication endpoint

- Implement JWT-based authentication
- Add login and logout routes
- Include password validation and hashing
- Set up middleware for protected routes
```

## Validation Rules

This skill helps ensure your commit message follows these rules:
1. Starts with exactly "Test App: "
2. Followed by a valid type from the list above
3. Optionally followed by scope in parentheses
4. Followed by ": " (colon and space)
5. Description in imperative mood (e.g., "add" not "added" or "adding")
6. Description under 50 characters
7. Description does not end with a period
8. First letter of description is capitalized

## Integration with Workflow

This skill is designed to be used after the workflow-skill passes:
1. Run `/workflow-skill` to check linting, tests, and code quality
2. Fix any issues reported
3. Run `/commit-skill` to help generate a proper commit message
4. Copy the generated message and use: `git commit -m "your message here"`
5. Push your changes

## Best Practices

- Use imperative mood in descriptions ("add" not "added" or "adding")
- Keep descriptions concise and under 50 characters
- Capitalize the first letter of the description
- Don't end descriptions with periods
- Reference issues/tickets when applicable (e.g., "Test App: fix: resolve login issue #123")
- Explain WHY in the commit body if needed (separate line after description)
- Avoid vague descriptions like "fix stuff" or "update code"
- Don't include file names in the description (they're in the diff)