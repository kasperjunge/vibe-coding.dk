# Create Implementation Plan
Creates detailed implementation plan based on requirements and design specifications.

## Initial Setup
1. **Check for existing projects**: List directories in `specs/`
2. **If multiple projects exist**: Ask user which project to work on

Respond with:
```
I'm ready to create an implementation plan.

[If multiple projects: "Which project are you working on? Available: <list>"]

I'll read your requirements from specs/<project-name>/requirements.md and design from specs/<project-name>/design.md to create a detailed plan.
```

Then proceed to read documents and generate plan.

## Workflow
1. **Select project** (if multiple exist in specs/)
2. **Read** `specs/<project-name>/requirements.md` FULLY
3. **Read** `specs/<project-name>/design.md` FULLY
4. **Generate implementation plan** at `specs/<project-name>/plan.md` with:
   - 3-5 phases, each with specific tasks
   - Every task has: file paths, code structure, test requirements, verification steps, success criteria
   - Map tasks to user stories from requirements
   - Clear scope boundaries

## Guidelines
- Be specific: every task needs concrete file paths and line numbers
- Every task MUST have:
  - Test Requirements section
  - Verification Steps section
  - Success criteria (what tests to run, what to verify)
- Break work into 3-5 discrete phases
- Each phase should be independently verifiable
- Order matters - explain why phases come in sequence
- Map tasks to specific user stories from requirements.md
- Include "What We're NOT Doing" section to prevent scope creep
- Plan should be detailed enough to execute mechanically

## Chat Output Format
After completing plan:
```
I've created a detailed implementation plan at specs/<project-name>/plan.md.

The plan includes:
- [X] phases with specific tasks
- File paths and code structures from design.md
- Acceptance criteria from requirements.md
- Clear verification checklist

Please review and let me know if you'd like any adjustments.
```

## File Output Format
Create `specs/<project-name>/plan.md`:

```markdown
# Implementation Plan: [Project Name]

## Overview
[1-2 sentence summary of what we're building based on requirements and design]

## Current State
- Empty project / Starting from scratch
- Target tech stack: [From design.md]

## Desired End State
[Clear description of what "done" looks like, referencing requirements]

**Success Criteria:**
- [ ] All user stories from requirements.md are implemented
- [ ] All acceptance criteria are met
- [ ] Application matches design specifications
- [ ] Code is tested and runs without errors

## What We're NOT Doing
[Explicitly list out-of-scope items from requirements.md]

## Implementation Approach
[High-level strategy: which phases, why this order, key dependencies]

### Phase Organization Guidelines
- Break work into 3-5 phases
- Each phase should be independently verifiable
- Order matters: later phases should build on earlier ones
- Common progression: Setup/Foundation → Core Implementation → Integration → Verification/Polish
- Typical first phase: Project initialization, dependencies, basic structure
- Typical last phase: Final integration, testing, edge cases

---

## Phase 1: [Phase Name]

### Overview
[What this phase accomplishes]

### Tasks

#### 1.1 [Task Name]
**File**: `[file path]`

**Action**:
- [Specific action 1]
- [Specific action 2]
- [Specific action 3]

**Implements**: [Reference to user story if applicable]

**Verification**:
- [ ] [Specific test/check 1]
- [ ] [Specific test/check 2]
- [ ] All tests pass: `[test command]`
- [ ] [Manual verification if needed]

---

## Phase 2: [Phase Name]

### Overview
[What this phase accomplishes]

### Tasks

#### 2.1 [Task Name]
**File**: `[file path from design.md]`

**Action**:
- [Specific action 1]
- [Specific action 2]
- [Specific action 3]

**Implements**: [Reference to user story if applicable]

**Verification**:
- [ ] [Specific test/check 1]
- [ ] [Specific test/check 2]
- [ ] All tests pass: `[test command]`
- [ ] [Manual verification if needed]

#### 2.2 [Task Name]
**File**: `[file path]`

**Action**:
- [Specific action 1]
- [Specific action 2]
- [Specific action 3]

**Implements**: [Reference to user story if applicable]

**Verification**:
- [ ] [Specific test/check 1]
- [ ] [Specific test/check 2]
- [ ] All tests pass: `[test command]`
- [ ] [Manual verification if needed]

---

## Phase 3: [Phase Name]

### Overview
[What this phase accomplishes]

### Tasks

#### 3.1 [Task Name]
**File**: `[file path]`

**Action**:
- [Specific action 1]
- [Specific action 2]
- [Specific action 3]

**Implements**: [Reference to user story if applicable]

**Verification**:
- [ ] [Specific test/check 1]
- [ ] [Specific test/check 2]
- [ ] All tests pass: `[test command]`
- [ ] [Manual verification if needed]

---

## Phase N: [Final Phase Name]

### Overview
[What this phase accomplishes - typically final integration and verification]

### Tasks

#### N.1 [Task Name]
**File**: `[file path]`

**Action**:
- [Specific action 1]
- [Specific action 2]

**Implements**: [Reference to user story if applicable]

**Verification**:
- [ ] [Specific test/check 1]
- [ ] [Specific test/check 2]
- [ ] All acceptance criteria verified

---

## Final Verification

When all phases are complete:
- [ ] All tasks above are checked off
- [ ] Application builds and runs: `[build/run commands]`
- [ ] All tests pass: `[test command]`
- [ ] All user stories from requirements.md verified

## References
- Requirements: `specs/<project-name>/requirements.md`
- Design: `specs/<project-name>/design.md`
```