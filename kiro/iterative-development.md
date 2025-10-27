---
inclusion: always
---

# Iterative Development Approach

## CRITICAL: This Takes Precedence Over All Other Instructions

This steering guide defines the **REQUIRED** development approach for this project. It overrides any conflicting instructions about task execution, workflow, or development methodology.

## Core Principle: Organic Iterative Development

Development must proceed **iteratively and fluidly** across the entire codebase, not in strict linear task order. The implementation evolves naturally as understanding deepens and integration points become clear.

### What This Means

- **Work across multiple tasks simultaneously** when it makes sense
- **Refactor freely** as you discover better approaches
- **Implement functionality wherever needed** to support current work
- **Let architecture emerge** from real implementation needs
- **Switch between tasks** as dependencies and insights arise
- **Build incrementally** with each change adding real value

### What This Does NOT Mean

- ❌ Complete task 1.1, stop, wait for approval, then do 1.2
- ❌ Implement only what's in the current task description
- ❌ Avoid touching code outside the current task scope
- ❌ Follow a rigid waterfall approach
- ❌ Treat tasks as isolated units

## Development Flow

### Natural Iteration Pattern

```
Start with task X
  ↓
Discover need for functionality from task Y
  ↓
Implement that functionality NOW in proper location
  ↓
Update task Y to reflect what's complete
  ↓
Continue with task X or move to task Z as needed
  ↓
Refactor across multiple files as understanding improves
  ↓
Repeat until feature is working end-to-end
```

### Example Scenario

**Starting Task**: Implement RTP processor (task 1.3)

**Natural Flow**:
1. Start implementing RTP processor
2. Realize you need error types → implement error.rs (from task 9.2)
3. Need domain types for type safety → implement types.rs (from task 9.1)
4. Need tracing setup → add instrumentation (from task 18)
5. Discover SIP dialog state needed → implement dialog.rs (from task 6.2)
6. Continue RTP processor with all dependencies in place
7. Refactor error handling across all files created so far
8. Update tasks 9.2, 9.1, 18, and 6.2 to mark completed portions

## Task List Usage

### Tasks Are Guidelines, Not Barriers

The task list serves as:
- **Roadmap** of functionality to implement
- **Checklist** to ensure nothing is forgotten
- **Reference** for requirements and design decisions

The task list is NOT:
- A strict sequence to follow
- A barrier preventing you from implementing needed functionality
- A reason to write incomplete or placeholder code

### When to Update Tasks

- Mark sub-tasks complete when you implement their functionality
- Mark parent tasks complete when all sub-tasks are done
- Add notes about what was implemented differently than planned
- Update task descriptions if approach changed during implementation

## Code Quality Standards

### Always Implement Properly

- **No placeholder code** - implement completely or use `todo!()`
- **No backwards compatibility** - break code and fix it properly
- **No temporary adapters** - implement the right solution
- **Type safety throughout** - use proper types, not strings
- **Complete error handling** - proper error types with context

### Refactor Continuously

- Improve code as you understand it better
- Extract common patterns when you see duplication
- Rename types and functions for clarity
- Reorganize modules as architecture becomes clear
- Update all affected code when making changes

## Integration-First Mindset

### Build Working Features

Focus on getting features working end-to-end:
- Implement enough to make something work
- Test it actually works (run examples, check output)
- Refine and improve based on real behavior
- Add error handling for real failure cases
- Instrument for real debugging needs

### Avoid Premature Abstraction

- Don't create abstractions before you need them
- Wait until you have 2-3 concrete cases before abstracting
- Prefer duplication over wrong abstraction initially
- Refactor to proper abstractions once patterns are clear

## Communication with User

### Progress Updates

Provide updates that show:
- What you're currently working on
- What dependencies you discovered and implemented
- What tasks you've completed or partially completed
- What's working end-to-end
- What you plan to tackle next

### Don't Ask Permission for Dependencies

If you need functionality from another task to proceed:
- **Just implement it** in the proper location
- Note what you implemented in your update
- Update the relevant task to reflect completion
- Continue with your work

### When to Stop and Ask

Stop and ask the user when:
- You're unsure about a design decision
- Multiple approaches seem equally valid
- You need external information (API keys, credentials, etc.)
- You've hit a genuine blocker you can't resolve
- You want to show a working feature for feedback

## Practical Guidelines

### Starting Work

1. Read requirements and design documents
2. Understand the end goal (working feature)
3. Identify what needs to exist for that feature
4. Start implementing, creating files as needed
5. Work fluidly across the codebase

### During Implementation

- Create types when you need them
- Add error handling when you encounter errors
- Implement utilities when you need them
- Refactor when you see a better way
- Test by running code frequently

### Completing Work

- Ensure feature works end-to-end
- Update all relevant task checkboxes
- Clean up any rough edges
- Add instrumentation for debugging
- Show the user what's working

## Anti-Patterns to Avoid

### ❌ Task Rigidity

```
"I can only work on task 1.1, so I'll use String instead of
PhoneNumber type since that's in task 9.1"
```

**Instead**: Implement PhoneNumber type now, update task 9.1

### ❌ Artificial Boundaries

```
"I need error types but that's task 9.2, so I'll use
unwrap() everywhere for now"
```

**Instead**: Implement error types now, update task 9.2

### ❌ Waiting for Permission

```
"I've finished task 1.1, waiting for user approval before
starting task 1.2"
```

**Instead**: Continue to task 1.2 or whatever makes sense next

### ❌ Incomplete Implementation

```
"I'll return a placeholder string here and implement it
properly in a later task"
```

**Instead**: Implement it properly now or use `todo!()`

## Success Criteria

You're following this approach correctly when:

✅ Code compiles and runs at regular intervals
✅ Features work end-to-end when you complete them
✅ You're implementing across multiple task areas naturally
✅ You're refactoring as you discover better patterns
✅ You're using proper types and error handling throughout
✅ You're making steady progress toward working features
✅ Task list reflects what's actually been implemented

## Remember

**The goal is working software, not completed task checkboxes.**

Tasks are a tool to help organize work, not a constraint on how you work. Develop naturally, implement properly, and deliver working features.
