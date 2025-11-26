# Exercise: Spec-Driven Development

In this exercise, you work in pairs to build a small project from scratch using **Spec-Driven Development** - a structured approach that separates requirements → design → planning → implementation stages with command-driven prompts.

Spec-Driven Development treats specification as the foundation that enables faster, more aligned implementation.

## Step-by-Step Instructions

### 1. Choose Project

**Select a project:**
Choose a small project that can be completed in a short session. Good candidates:
- Simple game (memory match, platformer mini-game, puzzle)
- Web app (todo list, notes app, job board)
- Utility tool (calculator, converter, data visualizer)

**Avoid:**
- Overly complex systems (defeats quick iteration)
- Trivial tasks (adding a single file)

### 2. Command Setup and Structure

**Create project folder:**
Create an empty project folder and open it in your AI coding tool.

**Setup commands:**
Copy the command files attached to this exercise to your AI tool's command directory:
- **Cursor**: Copy to `.cursor/commands/` in your project root
- **Claude Code**: Copy to `.claude/commands/` in your project root
- **GitHub Copilot**: Copy to `.github/prompts/` in your project root
  - **Note**: GitHub Copilot requires files to be named with `.prompt.md` extension
  - Rename files to: `clarify_requirements.prompt.md`, `clarify_design.prompt.md`, `create_plan.prompt.md`, `implement_plan.prompt.md`

Once copied, you can invoke them using `/clarify_requirements`, `/clarify_design`, `/create_plan`, and `/implement_plan`.

**Command structure:**
Each command has six sections: 

(1) Title & Description 
(2) Initial Setup - what the agent responds when invoked
(3) Workflow - step-by-step actions
(4) Guidelines - dos and don'ts
(5) Chat Output Format - what agent says to user
(6) File Output Format - template for generated files.

Skim the commmands to get a understanding of what they do.

### 3. Requirements Phase

**Objective:** Clarify what you're building and why - focus on user needs and value, not implementation.

**Start fresh:** Begin in a new chat session.

**Run the requirements command:**

```
/clarify_requirements
```

The agent will ask you to describe your project, then ask clarifying questions to understand the requirements fully. Answer the questions, and the agent will continue asking until it has no more questions. Then it will generate a structured requirements document at `spec/requirements.md` with user stories and acceptance criteria.

**Review the output:** Read through the generated requirements and ask the agent to make adjustments if anything doesn't align with your vision.

### 4. Design Phase

**Objective:** Clarify how you'll build it - tech stack, architecture, and implementation approach.

**Start fresh:** Start a new chat session.

**Run the design command:**

```
/clarify_design
```

The agent will read your requirements and ask you to describe your tech stack and design preferences. It will then ask clarifying questions to understand the technical approach fully. Answer the questions, and the agent will continue asking until it has no more questions. Then it will generate a design document at `spec/design.md` with architecture, components, and data models.

**Review the output:** Read through the design and ask the agent to make adjustments if anything doesn't match your technical vision.

### 5. Planning Phase

**Objective:** Break down the design into discrete, executable tasks.

**Start fresh:** Start a new chat session.

**Run the planning command:**

```
/create_plan
```

The command will generate an implementation plan at `spec/plan.md` with phases, specific tasks, and success criteria.

**Review the output:** Read through the plan and ask the agent to refine any phases that seem unclear or incomplete.

### 6. Implementation Phase

**Objective:** Execute the plan phase by phase.

**Start fresh:** Start a new chat session and switch to agent/composer mode.

**Run the implementation command:**

```
/implement_plan
```

The command will:
- Read `spec/plan.md` and check for existing progress
- Pick up from the first unchecked phase
- Implement each phase completely
- Run verification steps
- Update checkboxes in the plan as work completes
- Wait for your approval before proceeding to the next phase

**Key principles:**
- Verify each phase before proceeding to the next
- If implementation reveals spec issues, update specs first then continue
- If context fills up, start a new session and run `/implement_plan` again - it will pick up where it left off

### 7. Reflection and Documentation

**Review your artifacts:**
- `spec/requirements.md`
- `spec/design.md`
- `spec/plan.md`
- The implemented code

**Reflect on the process:**
- Did clear requirements lead to better design?
- Did clear design lead to better planning?
- Where did you catch the most important issues?
- How much time did upfront clarity save during implementation?

**Optional - Document learnings:**
Create `spec/learnings.md` to capture what worked and what didn't for future reference.

