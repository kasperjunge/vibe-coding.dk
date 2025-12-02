# Exercise: Spec-Driven Development

In this exercise, you work in pairs to build a small project from scratch using **Spec-Driven Development** - a structured approach that separates prototyping → requirements → design → planning → implementation stages with command-driven prompts.

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
  - Rename files to: `quick_prototype.prompt.md`, `clarify_requirements.prompt.md`, `clarify_design.prompt.md`, `create_plan.prompt.md`, `implement_plan.prompt.md`

Once copied, you can invoke them using `/quick_prototype`, `/clarify_requirements`, `/clarify_design`, `/create_plan`, and `/implement_plan`.

**Command structure:**
Each command has six sections: 

(1) Title & Description 
(2) Initial Setup - what the agent responds when invoked
(3) Workflow - step-by-step actions
(4) Guidelines - dos and don'ts
(5) Chat Output Format - what agent says to user
(6) File Output Format - template for generated files.

Skim the commands to get an understanding of what they do.

### 3. Prototyping Phase (Optional but Recommended)

> **This step is all about UI validation—get something on the screen fast, using fake or mock data. Do not spend too long or worry about correctness. The *entire* point is to have something visual to talk about and quickly iterate on, *not* to get it right the first time.**

**Objective:** Quickly explore and refine your idea through a working prototype.

**Start fresh:** Begin in a new chat session.

**Run the prototype command:**

```
/quick_prototype
```

The agent will:
- Ask you to describe your initial idea
- Infer a project name (e.g., "reading tracker" → "reading-tracker")
- Create directory structure: `specs/<project-name>/prototype/`
- Build a minimal working prototype
- Create `notes.md` to capture learnings during iteration

**Iterate on the prototype:** Try it out, give feedback, and let the agent make adjustments. The agent will continuously update `notes.md` with insights.

**When ready:** The agent will suggest moving to the formal spec-driven process.

### 4. Requirements Phase

**Objective:** Clarify what you're building and why - focus on user needs and value, not implementation.

**Start fresh:** Begin in a new chat session.

**Run the requirements command:**

```
/clarify_requirements
```

The agent will:
- Check if you have multiple projects in `specs/` and ask which to work on
- Read `specs/<project-name>/prototype/notes.md` if it exists (from prototyping phase)
- Ask clarifying questions to understand requirements fully
- Generate a structured requirements document at `specs/<project-name>/requirements.md` with user stories and acceptance criteria

**Review the output:** Read through the generated requirements and ask the agent to make adjustments if anything doesn't align with your vision.

### 5. Design Phase

**Objective:** Clarify how you'll build it - tech stack, architecture, and implementation approach.

**Start fresh:** Start a new chat session.

**Run the design command:**

```
/clarify_design
```

The agent will:
- Ask which project if multiple exist
- Read your requirements from `specs/<project-name>/requirements.md`
- Suggest a practical tech stack based on the requirements
- Ask clarifying questions to finalize the technical approach
- Generate a design document at `specs/<project-name>/design.md` with architecture, components, and data models

**Review the output:** Read through the design and ask the agent to make adjustments if anything doesn't match your technical vision.

### 6. Planning Phase

**Objective:** Break down the design into discrete, executable tasks.

**Start fresh:** Start a new chat session.

**Run the planning command:**

```
/create_plan
```

The agent will:
- Ask which project if multiple exist
- Read requirements and design documents
- Generate an implementation plan at `specs/<project-name>/plan.md` with phases, specific tasks, and success criteria

**Review the output:** Read through the plan and ask the agent to refine any phases that seem unclear or incomplete.

### 7. Implementation Phase

**Objective:** Execute the plan phase by phase.

**Start fresh:** Start a new chat session and switch to agent/composer mode.

**Run the implementation command:**

```
/implement_plan
```

The agent will:
- Ask which project if multiple exist
- Read `specs/<project-name>/plan.md` and check for existing progress
- Pick up from the first unchecked phase
- Implement each phase completely
- Run verification steps
- Update checkboxes in the plan as work completes
- Wait for your approval before proceeding to the next phase

**Key principles:**
- Verify each phase before proceeding to the next
- If implementation reveals spec issues, update specs first then continue
- If context fills up, start a new session and run `/implement_plan` again - it will pick up where it left off

### 8. Reflection and Documentation

**Review your artifacts:**
- `specs/<project-name>/prototype/notes.md` (if you did prototyping)
- `specs/<project-name>/requirements.md`
- `specs/<project-name>/design.md`
- `specs/<project-name>/plan.md`
- The implemented code

**Reflect on the process:**
- How did prototyping help clarify the concept?
- Did clear requirements lead to better design?
- Did clear design lead to better planning?
- Where did you catch the most important issues?
- How much time did upfront clarity save during implementation?

**Optional - Document learnings:**
Create `specs/<project-name>/learnings.md` to capture what worked and what didn't for future reference.

## Directory Structure

After completing all phases, your project should look like:

```
project-root/
├── specs/
│   └── <project-name>/
│       ├── prototype/           (if you did prototyping)
│       │   ├── notes.md
│       │   └── [prototype files]
│       ├── requirements.md
│       ├── design.md
│       └── plan.md
├── src/                         (actual implementation)
│   └── [your code files]
└── [other project files]
```

## Tips for Success

1. **Don't skip phases**: Each phase builds on the previous and catches different types of issues

2. **Start with prototyping for unclear ideas**: If you're not sure exactly what you want, start with `/quick_prototype` to explore

3. **Use fresh chats**: Starting each phase in a new chat prevents context pollution and keeps the agent focused

4. **Be thorough in early phases**: Time spent clarifying requirements and design saves multiples of that time in implementation

5. **Update specs when needed**: If implementation reveals issues, go back and update the relevant spec document

6. **Multiple projects**: The system supports multiple projects in `specs/` - commands will ask which one you're working on

## Workflow Variations

**Fast exploration → Formal build:**
1. `/quick_prototype` - Explore and iterate
2. `/clarify_requirements` - Formalize learnings
3. `/clarify_design` → `/create_plan` → `/implement_plan`

**Formal build from scratch:**
1. Skip prototyping
2. Start with `/clarify_requirements`
3. Continue with remaining phases

**Resume interrupted work:**
- All commands check for existing work and continue from where you left off
- Run the same command again in a new chat if you need to resume

