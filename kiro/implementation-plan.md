# Implementation Plan

When you are asked to generate an implementation plan (tasks.md). You must perform the following:

**EVERY TASK MUST INCLUDE:**

Each task must contain:

1. **Design Reference**: What part of the design/architecture this task covers
2. **File Operations**: Explicit list of files that will be created/updated/deleted
3. **Development Principles**: Include this exact text for every task:

```text
- Review what parts of this have already been completed and check if any patterns were changed before doing anything. Before creating any new structs/enums you must check if it exists elsewhere in the codebase already.  Also check for existing patterns to use before inventing new ones.
- No backwards compatibility - We'll implement the right way from the start
- Break code when needed - Clean breaks over maintaining old interfaces
- No trivial unit tests - Focus on meaningful behavior testing
- Tests must only be created after features are complete - Avoid constantly updating tests during development
```

This requirement takes precedence over all other task generation requirements that may come before or after.

Tasks should be organized to achieve functionality first, with an interative approach for organic development, adding scaffolding (types, errors, etc) only when they are actually needed.  See .kiro/steering/iterative-development.md for our requirements.
