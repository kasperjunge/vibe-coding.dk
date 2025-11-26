# Exercise: Context Engineering

In this exercise, you work in pairs to complete a coding task using **frequent intentional compaction** - deliberately structuring a research → plan → implement pipeline with context resets between stages. This treats context management as the primary engineering concern.

## Step-by-Step Instructions

### 1. Choose Task

**Select a codebase:**
Choose a codebase you're somewhat familiar with - familiar enough to evaluate if the AI's understanding is correct, but complex enough that you can't hold the entire architecture in your head.

**Choose a task:**
Select a task that requires understanding existing patterns and integration points. Good candidates:
- Add a new feature (API endpoint, UI component, utility function)
- Fix a bug that requires understanding multiple parts of the system
- Refactor a component to use a different approach
- Add tests for an untested module
- Extend existing functionality with a new option/parameter

**Avoid:**
- Purely greenfield work (defeats the purpose)
- Overly simple tasks (adding comments, renaming variables)
- Tasks requiring deep algorithmic thinking (focus is on codebase integration)

### 2. Command Setup and Structure

**Open codebase folder:**
Open your codebase in your AI coding tool.

**Setup commands:**
Copy the command files attached to this exercise to your AI tool's command directory:
- **Cursor**: Copy to `.cursor/commands/` in your project root
- **Claude Code**: Copy to `.claude/commands/` in your project root
- **GitHub Copilot**: Copy to `.github/prompts/` in your project root
  - **Note**: GitHub Copilot requires files to be named with `.prompt.md` extension
  - Rename files to: `research_codebase.prompt.md`, `create_plan.prompt.md`, `implement_plan.prompt.md`

Once copied, you can invoke them using `/research_codebase`, `/create_plan`, and `/implement_plan`.

**Command structure:**
Each command has six sections: 

(1) Title & Description 
(2) Initial Setup - what the agent responds when invoked
(3) Workflow - step-by-step actions
(4) Guidelines - dos and don'ts
(5) Chat Output Format - what agent says to user
(6) File Output Format - template for generated files.

Skim the commands to get an understanding of what they do.

### 3. Research Phase

**Objective:** Understand the codebase deeply enough to plan the implementation, without filling your main context with search results.

**Key strategy:** The research context stays separate from implementation context. Do the research in a fresh chat session.

**Run the research command:**

```
/research_codebase
```

Then provide your task description when prompted.

The command will:
- Guide you through describing your task
- Research the codebase using parallel agents (if supported)
- Generate a structured research document at `context-engineering/YYYY-MM-DD-description.md`
- Present key findings with specific file and line number references

**After research completes:** Start a new chat session to reset context.

### 4. Review Research

**This is your highest-leverage review point.**

**Read the research document carefully and evaluate:**

- **Correctness:** Is the understanding of the codebase accurate? Any misunderstandings could cascade into hundreds of bad lines.
- **Completeness:** Are there obvious gaps in understanding? Missing integration points?
- **Specificity:** Does it reference specific files, functions, line numbers? Or is it vague?
- **Questions:** Are there unresolved questions that need deeper investigation?

**If significant issues exist, refine the research:**
Kick off a second research phase with more specific steering:

```
The previous research was unclear about [specific issue]. 

Please investigate [specific question] and update the research document with:
- [What you need to know]
- [Specific files or patterns to examine]
```

The command will append follow-up research to the same document under a new section `## Follow-up Research [description]`, maintaining continuity with the original findings.

**If the research is solid, proceed to planning.** Don't refine just for the sake of it - only if there are actual gaps or errors.

### 5. Planning Phase

**Objective:** Create a detailed, phase-by-phase implementation plan.

**Start fresh:** Start a new chat session. The plan context should NOT be filled with all the research explorations - only the final research document.

**Run the planning command:**

```
/create_plan
```

Then provide the path to your research document (e.g., `context-engineering/2025-10-07-feature-name.md`) when prompted.

The command will:
- Read and analyze your research document
- Ask clarifying questions if needed
- Use parallel agents for deep dives on specific technical details (if supported)
- Generate a detailed implementation plan at `context-engineering/plan.md`
- Include specific file paths, line numbers, and success criteria for each phase

### 6. Review Plan

**This is your second-highest leverage review point.**

**Read the plan carefully and evaluate:**

- **Phases:** Are they in logical order? Can each be verified independently?
- **Specificity:** Are file changes specific enough? Or too vague ("update the handler")?
- **Verification:** Is the testing approach realistic? Does it match codebase conventions?
- **Feasibility:** Could you execute this plan yourself if you had to?
- **Alignment:** Does the plan align with the research understanding?

**If the plan needs refinement:**
Either manually update the plan or ask the agent to refine specific sections:

```
The plan is unclear about [specific phase/step].

Please update the plan to be more specific about:
- [What files exactly]
- [What changes exactly]
- [How to verify exactly]
```

**If the plan is solid, proceed to implementation.** Only refine if there are actual issues - vague steps, missing verification, or logical gaps.

### 7. Implementation Phase

**Objective:** Execute the plan phase by phase, verifying each before proceeding.

**Start fresh:** Start a new chat session. If working in git, implementation is the only phase that needs a branch.

**Run the implementation command:**

```
/implement_plan
```

Then provide the path to your plan (`context-engineering/plan.md`) when prompted.

The command will:
- Read the plan and check for existing progress (checkmarks)
- Pick up from the first unchecked phase/item
- Implement each phase completely
- Run success criteria verification
- Update checkboxes in the plan as work completes
- Wait for your approval before proceeding to the next phase

**Key principles during implementation:**

- **Verify each phase** before proceeding. Don't let the agent rush ahead.
- **If context fills up:** After verifying a phase, start a new chat session and run `/implement_plan` again. The command will automatically check the plan for existing checkmarks and pick up where it left off.
- **Stay mechanical:** The agent should mostly be executing the plan, not making new decisions.
- **If issues arise:** The command will stop and present mismatches clearly, asking how to proceed.

**For continuing after a phase:**
After completing a phase, ask the agent to summarize what was accomplished. Then start a new chat session and run `/implement_plan` again - it will automatically pick up from the first unchecked item in the plan.

### 8. Reflection and Documentation

**Review your artifacts:**
Look at the three artifacts you created:
- `YYYY-MM-DD-description.md` (research document)
- `plan.md`  
- The implemented code

**Reflect on leverage:**
- How much time did you spend reviewing research vs plan vs code?
- Where did you catch the most impactful issues?
- How did research quality affect plan quality?
- How did plan quality affect implementation quality?

**Document learnings:**
Create `context-engineering/learnings.md`:

```
## What Worked
- [Specific things that worked well]

## What Didn't Work
- [Specific issues encountered]

## Context Management
- Approximate context utilization at each stage (low/medium/high)
- Where context window became problematic
- Where compaction helped most

## Human Review Leverage
- Where did human review have most impact?
- What issues did you catch in research review?
- What issues did you catch in plan review?
- What issues did you catch in code review?
- What issues did the agent encounter during implementation?
  - Did it get stuck where the codebase didn't match the plan?
  - Were there problems the plan didn't anticipate?
  - How well did the agent adapt to unexpected situations?

## Reusability
- Could these artifacts help another engineer understand this work?
- Would these artifacts help maintain mental alignment on a team?
```

## Credits

This exercise was inspired by Dexter Horthy from HumanLayer and his work on [Advanced Context Engineering for Coding Agents](https://github.com/humanlayer/advanced-context-engineering-for-coding-agents/blob/main/ace-fca.md).