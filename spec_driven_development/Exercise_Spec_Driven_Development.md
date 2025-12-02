# Exercise: Spec-Driven Development

In this exercise, you work in pairs to build a small project from scratch using **Spec-Driven Development** - a structured approach that separates prototyping → requirements → design → planning → implementation stages with command-driven prompts.

Spec-Driven Development treats specification as the foundation that enables faster, more aligned implementation.

## Step-by-Step Instructions

### 1. Choose Project

**Select a project:**
Choose a small project that can be completed in a short session. Good candidates:
- Game (memory match, platformer mini-game, puzzle)
- Web app (todo list, notes app, job board)
- Utility tool (calculator, converter, data visualizer)

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
- Infer a project name
- Create directory structure: `specs/<project-name>/prototype/`
- Build a minimal working prototype
- Create `notes.md` to capture learnings during iteration

**Iterate on the prototype:** Try it out, give feedback, and let the agent make adjustments. The agent will continuously update `notes.md` with learnings.

**When ready:** The agent will suggest moving to the formal spec-driven process.

### 4. Requirements Phase

**Objective:** Clarify what you're building and why - focus on user needs and value, not implementation.

**Start fresh:** Begin in a new chat session.

**Run the requirements command:**

```
/clarify_requirements
```

The agent will:
- Read `specs/<project-name>/prototype/notes.md` if it exists (from prototyping phase)
- Ask clarifying questions to understand requirements fully
- Generate a structured requirements document at `specs/<project-name>/requirements.md` with user stories and acceptance criteria

**Review the output:** Skim through the generated requirements and ask the agent to make adjustments if anything doesn't align with your vision.

### 5. Design Phase

**Objective:** Clarify how you'll build it - tech stack, architecture, and implementation approach.

**Start fresh:** Start a new chat session.

**Run the design command:**

```
/clarify_design
```

The agent will:
- Read your requirements from `specs/<project-name>/requirements.md`
- Suggest a practical tech stack based on the requirements
- Ask clarifying questions to finalize the technical approach
- Generate a design document at `specs/<project-name>/design.md` with architecture, components, and data models

**Review the output:** Skim through the design and ask the agent to make adjustments if anything doesn't match your technical vision.

### 6. Planning Phase

**Objective:** Break down the design into discrete, executable tasks.

**Start fresh:** Start a new chat session.

**Run the planning command:**

```
/create_plan
```

The agent will:
- Read requirements and design documents
- Generate an implementation plan at `specs/<project-name>/plan.md` with phases, specific tasks, and success criteria

**Review the output:** Skim through the plan and ask the agent to refine any phases that seem unclear or incomplete.

### 7. Implementation Phase

**Objective:** Execute the plan phase by phase.

**Start fresh:** Start a new chat session.

**Run the implementation command:**

```
/implement_plan
```

The agent will:
- Read `specs/<project-name>/plan.md` and check for existing progress
- Pick up from the first unchecked phase
- Implement the phase completely
- Run verification steps
- Update checkboxes in the plan as work completes
- **Stop and wait for your review**

**After each phase:**
1. Review the implemented code and test results
2. Verify any manual checks listed by the agent
3. **Start a new chat** and run `/implement_plan` again for the next phase

Continue until the agent completes the project and then prep for demo 🚀
