# CLAUDE.md - AI Development Guidelines

This file specifies development practices and workflows for AI-assisted software development in this repository.

## Work Tracking

All work is tracked through Jira. When working on tasks:
- Reference Jira ticket numbers in commits and PRs
- Update ticket status as work progresses
- Link relevant code changes to tickets

## Development Philosophy

### Research-First Approach

Before implementing any solution:
1. **Research** existing code patterns and architecture
2. **Analyze** the problem domain thoroughly
3. **Identify** potential impacts and dependencies
4. **Document** findings and proposed approach

### Planning & Approval

**Always plan before implementing:**
1. Present a detailed plan outlining:
   - Problem analysis
   - Proposed solution architecture
   - Implementation steps
   - Testing strategy
   - Potential risks or impacts
2. Wait for user approval before proceeding with implementation
3. Adjust plan based on feedback

## File Management

### No Unsolicited File Creation

**Critical Rule**: Never create new files unless explicitly requested by the user.

- Prefer modifying existing files over creating new ones
- If a new file seems necessary, ask for permission first
- Explain why a new file is needed and wait for approval
- This includes:
  - Documentation files (README, *.md)
  - Configuration files
  - New source code files
  - Test files (unless specifically following TDD workflow)

## Code Quality Standards

### Core Principles

- **Modular**: Break functionality into small, focused modules
- **DRY (Don't Repeat Yourself)**: Abstract common functionality, eliminate duplication
- **Single Responsibility**: Each function/class should have one clear purpose

### Expand-Refactor-Contract Pattern

When updating existing software:
1. **Expand**: Add new functionality alongside existing code
2. **Refactor**: Gradually migrate usage to new implementation
3. **Contract**: Remove old code once migration is complete

This approach ensures:
- Backward compatibility during transitions
- Safe rollback if issues arise
- Gradual validation of changes

## Version Control

### Conventional Commits

Use the Conventional Commits specification for all commit messages:

**Format**: `<type>[optional scope]: <description>`

**Types**:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, semicolons, etc.)
- `refactor`: Code changes that neither fix bugs nor add features
- `perf`: Performance improvements
- `test`: Adding or modifying tests
- `build`: Build system or dependency changes
- `ci`: CI/CD configuration changes
- `chore`: Other changes that don't modify src or test files
- `revert`: Reverts a previous commit

**Examples**:
```
feat(auth): add OAuth2 integration
fix(api): handle null response in user endpoint
docs: update API documentation
refactor(utils): simplify date formatting logic
test(auth): add unit tests for login flow
```

**Breaking Changes**: Add `!` after type/scope or include `BREAKING CHANGE:` in footer
```
feat(api)!: change response format for user endpoint
```

## Test-Driven Development (TDD)

Follow TDD practices whenever possible:

1. **Write Tests First**
   - Define expected behavior through tests
   - Tests should initially fail (red phase)
   - Cover edge cases and error scenarios

2. **Implement Minimal Code**
   - Write just enough code to pass tests (green phase)
   - Focus on making tests pass, not perfection

3. **Refactor**
   - Improve code quality while maintaining passing tests
   - Apply DRY and Single Responsibility principles
   - Ensure modularity

### Testing Guidelines

- Unit tests for individual functions/methods
- Integration tests for component interactions
- End-to-end tests for critical user flows
- Maintain high test coverage (aim for >80%)

### When working you MUST FOLLOW the following Architecture Principals:  
- KISS (Keep It Simple, Stupid)
- YAGNI (You Aren't Gonna Need It)
- SOLID Principles
- TTD (Test Driven Development)

## Workflow Summary

1. **Receive Jira ticket** → Research codebase and problem domain
2. **Present plan** → Wait for approval
3. **Write failing tests** → Define expected behavior
4. **Implement solution** → Following modular, DRY principles
5. **Make tests pass** → Validate implementation
6. **Refactor if needed** → Using expand-refactor-contract pattern
7. **Update Jira** → Document completion and any follow-up items

## Communication

- Be explicit about which phase of work you're in
- Provide clear rationale for technical decisions
- Ask for clarification when requirements are ambiguous
- Report blockers or concerns early
- Always ask before creating new files
