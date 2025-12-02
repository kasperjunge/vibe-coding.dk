# Clarify Requirements
Helps clarify project requirements by asking focused questions and documenting user needs.

## Initial Setup
1. **Check for existing projects**: List directories in `specs/`
2. **If multiple projects exist**: Ask user which project to work on
3. **Check for prototype notes**: Look for `specs/<project-name>/prototype/notes.md`

**If notes.md exists**, respond with:
```
I'm ready to help clarify your project requirements.

I found prototype notes at specs/<project-name>/prototype/notes.md. I'll use these as a starting point.

Let me read the notes and then we'll clarify the requirements together.
```

**If no prototype exists**, respond with:
```
I'm ready to help clarify your project requirements.

Please describe what you want to build.
```

Wait for user input.

## Workflow
1. **Select project** (if multiple exist in specs/)
2. **Read prototype notes** (if `specs/<project-name>/prototype/notes.md` exists)
3. **Optionally read prototype code** (if helpful for context, read files in `specs/<project-name>/prototype/`)
4. **Receive user's project description** (or use notes as starting point)
5. **Ask clarifying questions** (2-3 at a time, **maximum 2 rounds**) focusing on:
   - Core user goal and primary use case
   - Scope boundaries (what's explicitly out)
   - One key scenario if unclear
6. **Stop after 2 rounds** - make reasonable assumptions for anything unclear and document them
7. **Generate requirements document** at `specs/<project-name>/requirements.md`

## Guidelines
- **Aim for "good enough", not perfect**: Get enough information to start - specs can be refined later
- **Avoid rabbit holes**: Don't explore every edge case in depth - note them and move on
- **Bias toward action**: When in doubt, make a reasonable assumption and document it rather than asking another question
- **Time target**: This phase should take ~5-10 minutes, not 30+
- Each bullet with a clarifying question should be numbered
- Stay user-focused: describe WHAT users need, not HOW to build it
- No tech stack, architecture, or implementation details
- Be specific: acceptance criteria should be testable
- Use "Out of Scope" section aggressively to prevent scope creep
- Every feature should map to a clear user need
- If prototype code exists, you may read it for additional context beyond notes.md if helpful

## Chat Output Format
After completing requirements:
```
I've created a requirements document at specs/<project-name>/requirements.md.

The document includes:
- [X] user stories with acceptance criteria
- [X] functional requirements  
- Non-functional requirements
- Clear scope boundaries

[If prototype notes existed:]
I've incorporated insights from the prototype notes into the requirements.

Please review and let me know if you'd like any adjustments.
```

## File Output Format
Create `specs/<project-name>/requirements.md`:

```markdown
# Requirements: [Project Name]

## Project Overview
[2-3 sentences describing what this project is and why it exists]

## Target Users
[Who will use this? What's their context and needs?]

## User Stories

### Story 1: [User Goal]
**As a** [type of user]  
**I want to** [action]  
**So that** [benefit/value]

**Acceptance Criteria:**
- [ ] [Specific, testable criterion 1]
- [ ] [Specific, testable criterion 2]
- [ ] [Specific, testable criterion 3]

**Edge Cases:**
- [What happens when X?]
- [What happens when Y?]

### Story 2: [Another User Goal]
[Same structure as Story 1]

[Continue for all major user stories]

## Functional Requirements

### FR1: [Requirement Name]
**Description**: [What the system must do]  
**Priority**: High/Medium/Low  
**Acceptance**: [How to verify this works]

### FR2: [Another Requirement]
[Same structure]

## Non-Functional Requirements

### Performance
- [e.g., "Page load time under 2 seconds"]
- [e.g., "Support up to 1000 items"]

### Usability
- [e.g., "Interface should be intuitive for first-time users"]
- [e.g., "Key actions accessible within 2 clicks"]

### Accessibility
- [Any accessibility requirements if applicable]

## Out of Scope
[Explicitly list what we're NOT building to prevent scope creep]
- [Feature/functionality 1]
- [Feature/functionality 2]

## Success Criteria
[How do we know this project succeeded?]
- [ ] [Measurable success criterion 1]
- [ ] [Measurable success criterion 2]
```