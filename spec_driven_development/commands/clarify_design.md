# Clarify Design
Clarifies technical design and architecture based on requirements.

## Initial Setup
1. **Check for existing projects**: List directories in `specs/`
2. **If multiple projects exist**: Ask user which project to work on
3. **Read requirements document fully**
4. **Suggest simple tech stack** based on requirements

Respond with:
```
I'm ready to help clarify the technical design.

[If multiple projects: "Which project are you working on? Available: <list>"]

I've read your requirements from specs/<project-name>/requirements.md.

Based on the requirements, I suggest this tech stack:

**Languages & Frameworks:**
- [Suggest appropriate, practical framework]
- [Key libraries/tools needed]

**Data & State:**
- [Storage/state management approach]

Does this work for you, or would you prefer something different?
```

Wait for user input and adjust based on their feedback.

## Workflow
1. **Select project** (if multiple exist in specs/)
2. **Read** `specs/<project-name>/requirements.md` FULLY
3. **Optionally read prototype code** (if helpful for context, read files in `specs/<project-name>/prototype/`)
4. **Suggest practical tech stack** based on requirements (avoid over-engineering)
5. **Receive user's feedback** on the suggestion (accept, modify, or propose alternative)
6. **Ask clarifying questions** (2-3 at a time, **maximum 2 rounds**) focusing on:
   - Architecture patterns (only if not clear from tech stack choice)
   - Data storage approach (only if not obvious)
7. **Stop after 2 rounds** - make reasonable assumptions for anything unclear and document them
8. **Generate design document** at `specs/<project-name>/design.md`

## Guidelines
- **Aim for "good enough", not perfect**: Get enough information to start - design can be refined later
- **Avoid rabbit holes**: Don't explore every architectural option - pick sensible defaults and move on
- **Bias toward action**: When in doubt, make a reasonable assumption and document it rather than asking another question
- **Time target**: This phase should take ~5-10 minutes, not 30+
- **Suggest practical stack**: Propose an appropriate, uncomplicated tech stack that fits requirements
- **Avoid over-engineering**: Match tech choices to actual needs, not theoretical scale
- **Consider prototype**: If prototype exists and works well, suggest building on its tech choices
- **Don't justify simplicity**: Just suggest the stack, don't explain why it's simple or easy
- Each bullet with a clarifying question should be numbered
- Be specific: name actual technologies with versions, not placeholders
- Align with requirements: every design decision should trace back to requirements
- If user doesn't mention UI approach and requirements need one, suggest based on requirements
- If user has no testing preferences, create appropriate strategy based on tech stack
- Include concrete file/folder structures
- Match complexity to project scope
- If prototype code exists, you may read it for additional context if helpful

## Chat Output Format
After completing design:
```
I've created a design document at specs/<project-name>/design.md.

The design includes:
- Complete tech stack with rationale
- Component breakdown with responsibilities
- Data model and UI structure
- Key user flows and interactions
- File structure and development approach

Please review and let me know if you'd like any adjustments.
```

## File Output Format
Create `specs/<project-name>/design.md`:

```markdown
# Design: [Project Name]

## Design Overview
[2-3 sentences describing the technical approach and key architectural decisions]

## Tech Stack

### Languages & Frameworks
- **Language**: [e.g., JavaScript/TypeScript]
- **Framework**: [e.g., React 18]
- **Build Tool**: [e.g., Vite]
- **Styling**: [e.g., Tailwind CSS]

### Data & State
- **Data Storage**: [e.g., localStorage, PostgreSQL, MongoDB]
- **State Management**: [e.g., React Context, Redux, Zustand]
- **Data Format**: [e.g., JSON, structured data model]

### Dependencies
- [Library 1]: [Purpose]
- [Library 2]: [Purpose]

**Rationale**: [Why this tech stack? How does it fit the requirements?]

## Architecture & Components

### Component: [Name]
**Purpose**: [What this component does]  
**Location**: `src/components/ComponentName.tsx`  
**Responsibilities**:
- [Responsibility 1]
- [Responsibility 2]
- [Responsibility 3]

## Data Model

### Entity: [EntityName]
```typescript
interface EntityName {
  id: string;
  field1: string;
  field2: number;
  field3: Date;
}
```

**Purpose**: [What this represents]  
**Relationships**: [How it relates to other entities]

## User Interface

### Screen: [ScreenName]
**Purpose**: [What user accomplishes here]  
**Key Elements & Interactions**:
- [Element 1]: [Purpose] → [User interaction and result]
- [Element 2]: [Purpose] → [User interaction and result]
- [Element 3]: [Purpose] → [User interaction and result]

## Key User Flows

### Flow: [FlowName]
**Implements**: [User story from requirements]

1. User [action]
2. System [response]
3. User sees [result]

**Error Handling**: [How errors are handled in this flow]

## File Structure
```
project-root/
├── src/
│   ├── components/
│   │   ├── ComponentA.tsx
│   │   └── ComponentB.tsx
│   ├── hooks/
│   │   └── useCustomHook.ts
│   ├── utils/
│   │   └── helpers.ts
│   ├── types/
│   │   └── index.ts
│   ├── App.tsx
│   └── main.tsx
├── spec/
│   ├── requirements.md
│   └── design.md
├── package.json
└── README.md
```

## Implementation Notes

### Key Design Decisions
- [Decision 1]: [Why we chose this approach]
- [Decision 2]: [Why we chose this approach]

### Non-Functional Requirements
- **Performance**: [Key performance considerations]
- **Accessibility**: [Accessibility approach if required]
- **Error Handling**: [How errors are caught and displayed to users]

## Testing Approach

### Testing Tools
- **Framework**: [e.g., Vitest, Jest, pytest]
- **Run Command**: `[e.g., npm test, pytest]`

### Testing Strategy
- [When to write tests: TDD / test-after / incremental]
- [What to test: unit tests for logic, component tests for UI, integration tests for flows]
- [Manual verification needed for: visual appearance, UX flows]

## References
- Requirements: `specs/<project-name>/requirements.md`
- [Any relevant documentation or resources]
```
