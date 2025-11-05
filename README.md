# Vibe Coding Community Resources

Command-driven workflows for better AI pair programming from [vibe-coding.dk](https://vibe-coding.dk).

## What's Inside

Two structured approaches for AI-assisted development:

### 🎯 Spec-Driven Development
Build projects from scratch with clarity: requirements → design → plan → implementation.

**Best for:** Greenfield projects where you're starting from zero.

**Commands:** `clarify_requirements`, `clarify_design`, `create_plan`, `implement_plan`

### 🔍 Research-Plan-Implement
Work with existing codebases: research → plan → implement with fresh context at each stage.

**Best for:** Existing codebases where you need to understand patterns and integrate changes.

**Commands:** `research_codebase`, `create_plan`, `implement_plan`

## Quick Start

### For Cursor
```bash
cp spec_driven_development/commands/* .cursor/commands/
# or
cp research_plan_implement/commands/* .cursor/commands/
```

### For Claude Code
```bash
cp spec_driven_development/commands/* .claude/commands/
# or
cp research_plan_implement/commands/* .claude/commands/
```

### For GitHub Copilot
```bash
mkdir -p .github/prompts
cp spec_driven_development/commands/* .github/prompts/

# Rename to .prompt.md extension
cd .github/prompts
for f in *.md; do mv "$f" "${f%.md}.prompt.md"; done
```

## Usage

Once commands are installed, invoke them in chat:

```
/clarify_requirements
/research_codebase
/implement_plan
```

Each command guides you through its workflow with clear prompts and generates structured documentation.

## Philosophy

**Spec-Driven Development** treats specification as the foundation—clear requirements and design enable faster, more aligned implementation.

**Research-Plan-Implement** treats context as the primary constraint—intentional compaction at each stage prevents context pollution and maintains focus.

Both approaches separate thinking from doing, review from execution.

## Learn More

Full exercises and guidance available at [vibe-coding.dk](https://vibe-coding.dk).

---

*Keep it simple. Vibe with your AI.*
