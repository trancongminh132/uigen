# Commit Message Formatting Skill

This skill helps you format commit messages consistently with the "Test App: " prefix as required by your project standards.

## How to Use

When creating a commit, follow this format:
```
Test App: <type>(<scope>): <description>
```

## Commit Message Format

### Structure
```
Test App: <type>(<scope>): <description>
```

#### Elements:
- **Test App: ** - Required prefix for all commits in this project
- **<type>** - The type of change (feat, fix, docs, style, refactor, test, chore, etc.)
- **<scope>** - Optional: the part of the codebase affected (component, api, ui, etc.)
- **<description>** - Brief summary of the change (imperative mood, max 50 chars)

### Types
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

### Examples
- `Test App: feat(ui): add card component with title and action button`
- `Test App: fix(auth): resolve sign-in form validation error`
- `Test App: docs: update README with setup instructions`
- `Test App: style: format components according to eslint rules`
- `Test App: refactor(api): extract user service to separate module`
- `Test App: test: add unit tests for badge component`
- `Test App: chore: update dependencies to latest versions`

## Best Practices

### Do:
- Use imperative mood ("add" not "added" or "adding")
- Keep description under 50 characters
- Capitalize first letter of description
- Don't end description with period
- Reference issues/tickets when applicable (e.g., "Test App: fix: resolve login issue #123")
- Explain WHY in the commit body if needed (separate line after description)

### Don't:
- Use vague descriptions like "fix stuff" or "update code"
- Include file names in the description (they're in the diff)
- Use all caps or excessive punctuation
- Make description too long (aim for 50 chars max)

## Commit Body (Optional)
For complex changes, add a body after a blank line:
```
Test App: feat(api): add user authentication endpoint

- Implement JWT-based authentication
- Add login and logout routes
- Include password validation and hashing
- Set up middleware for protected routes
```

## Validation
Before committing, verify your message:
1. Starts with "Test App: "
2. Follows conventional commit format
3. Describes the change clearly and concisely
4. Uses appropriate type and scope

## Hook Integration
Consider setting up a commit-msg hook to automatically validate commit messages follow this format.