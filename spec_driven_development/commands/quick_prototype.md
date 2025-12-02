# Quick Prototype
Creates a minimal working prototype from a rough idea to explore and refine the concept through conversation.

## Initial Setup
Respond with:
```
I'm ready to help you explore your idea with a quick prototype.

This is about speed and experimentation - we'll build something minimal that works so you can see your idea in action and refine it through conversation.

Please describe your initial idea (even if it's rough or incomplete).
```

Wait for user input.

## Workflow
1. **Receive user's rough idea**
2. **Infer project name** from description (e.g., "reading tracker" → "reading-tracker")
3. **Create directory structure**:
   - Create `specs/<project-name>/prototype/`
   - Create empty `specs/<project-name>/prototype/notes.md`
4. **Make educated assumptions** about:
   - The simplest tech stack that gets it working fast
   - Core interaction (what's the one thing users do?)
   - Minimal feature set (what's the bare minimum to demonstrate the idea?)
5. **Propose prototype scope** (2-3 sentences):
   - What you'll build
   - What tech you'll use
   - What will be deliberately rough/incomplete
6. **Wait for approval or adjustments**
7. **Build the prototype** (aim for < 15 minutes of work):
   - All files go in `specs/<project-name>/prototype/`
   - Single file or minimal file structure
   - Inline styles (no separate CSS unless requested)
   - Mock data if needed
   - Focus on the core interaction
8. **Create initial notes.md** with:
   - Project name and concept
   - Initial assumptions and decisions
9. **Provide instructions** to run it
10. **Start conversation** to refine the idea
11. **Update notes.md continuously** as insights emerge during conversation

## Guidelines
- **Speed over quality**: Use the fastest path to something working
- **Minimal viable demo**: Just enough to see the idea in action
- **Make assumptions boldly**: Don't ask about tech stack unless user has strong preferences
- **One core interaction**: What's the main thing users do? Start there
- **No architecture**: Single file is fine, inline everything is fine
- **Visual preferred**: If it's visual, make it visual (even if ugly)
- **Runnable immediately**: Should work with a single command (npm run dev, python app.py, etc.)
- **Mock liberally**: Hard-code data, skip APIs, fake authentication
- **No tests, no docs**: This is exploration, not production
- **Capture learnings**: Update `notes.md` after each significant insight or decision during conversation

## Prototype Defaults
Unless user specifies otherwise:
- **Web apps**: HTML + vanilla JS (or Vite + React if interactivity is complex)
- **Games**: HTML Canvas or simple game library
- **CLI tools**: Python or Node.js
- **Data viz**: HTML + simple charting library
- **Styling**: Tailwind CDN or inline styles

## Chat Output Format
After building prototype:
```
I've created a quick prototype for "[Project Name]".

**Location:** specs/<project-name>/prototype/

**What it does:**
- [Core feature 1]
- [Core feature 2]

**To run it:**
1. cd specs/<project-name>/prototype/
2. [Installation command if needed]
3. [Run command]
4. Open [URL or instructions]

**What's deliberately rough:**
- [Thing 1 we're skipping]
- [Thing 2 that's hard-coded]
- [Thing 3 that needs work]

I've created notes.md to capture what we learn during this exploration.

Try it out! Then let's talk about:
- What feels right?
- What's missing?
- What should work differently?
- What would make this more useful?

Based on your feedback, we can iterate on this prototype or move to the full spec-driven process (/clarify_requirements).
```

## Conversation Guidelines
After prototype is running:

1. **Ask open questions**:
   - "What's your first reaction?"
   - "What would you want to do next that you can't do now?"
   - "What feels wrong about this?"
   
2. **Listen for:**
   - Features they try to use that don't exist
   - Confusion about purpose or interaction
   - Excitement about specific aspects
   - Concerns about scope or complexity

3. **Iterate quickly**:
   - Make small changes based on feedback
   - Add one feature at a time
   - Remove things that don't resonate
   - Pivot if the idea evolves

4. **Update notes.md after each insight**:
   - Add bullet points for new learnings
   - Document feature requests or changes
   - Note what worked vs what didn't
   - Capture user preferences and priorities

5. **Know when to graduate**:
   When the idea feels solid, suggest:
   ```
   This prototype has helped clarify your vision! 
   
   I think we're ready to move to the structured process:
   - Run /clarify_requirements to document what we've learned
   - Then follow the full spec-driven development workflow
   
   Or we can keep iterating on the prototype if you want to explore more.
   ```

## File Organization
```
specs/
└── <project-name>/
    └── prototype/
        ├── notes.md           (learnings captured during iteration)
        ├── index.html         (for web apps)
        ├── app.js             (or app.py, main.js, etc.)
        └── package.json       (if dependencies needed)
```

Alternative minimal structure:
```
specs/
└── <project-name>/
    └── prototype/
        ├── notes.md
        └── prototype.html     (everything inline)
```

## Example Interactions

### Example 1: Web App
**User**: "I want to build something to track my reading habits"

**Response**:
```
I'll create a prototype called "reading-tracker".

Directory structure:
specs/reading-tracker/prototype/

I'll build a quick prototype that lets you:
- Add books you're reading
- Mark progress (started, reading, finished)
- See your reading list

I'll use: HTML + vanilla JS + localStorage (no build step needed)

This will be rough - no styling polish, no editing/deleting, hard-coded categories. Just the core interaction.

I'll capture our learnings in notes.md as we iterate.

Sound good?
```

### Example 2: Game
**User**: "A simple word guessing game"

**Response**:
```
I'll create a prototype called "word-guess-game".

Directory structure:
specs/word-guess-game/prototype/

I'll build a minimal version where:
- Player guesses letters in a hidden word
- See which letters are correct
- Win/lose states

I'll use: HTML + vanilla JS with simple UI

This will be basic - no difficulty levels, small word list, simple graphics. Just the core game loop.

I'll capture our learnings in notes.md as we iterate.

Ready to proceed?
```

## Anti-Patterns
❌ Don't ask about requirements, user stories, or acceptance criteria
❌ Don't propose architecture or file structures beyond minimal
❌ Don't discuss testing strategy or CI/CD
❌ Don't create comprehensive documentation
❌ Don't spend time on code quality or best practices
❌ Don't build production-ready features

✅ Do make quick decisions
✅ Do use the simplest tools
✅ Do hard-code and mock aggressively
✅ Do focus on the core interaction
✅ Do iterate based on feedback
✅ Do graduate to spec-driven process when ready

## Transition to Spec-Driven Development
When the prototype has served its purpose:

```
Great! We've explored your idea through this prototype and learned:
- [Key insight 1]
- [Key insight 2]
- [Key insight 3]

I've captured all our learnings in specs/<project-name>/prototype/notes.md.

Now let's build this properly using spec-driven development:

1. Start a new chat and run `/clarify_requirements`
   - It will read notes.md as a starting point
   - We'll define clear user stories and acceptance criteria
   - Output: specs/<project-name>/requirements.md
   
2. Then run `/clarify_design`
   - Choose production-appropriate tech stack
   - Design proper architecture
   - Output: specs/<project-name>/design.md
   
3. Then `/create_plan` and `/implement_plan`
   - Build it right with tests and quality
   - Output: specs/<project-name>/plan.md

The prototype helped us answer "what" - now let's answer "how" properly!
```

## Notes.md Format
Create and update `specs/<project-name>/prototype/notes.md`:

```markdown
# Prototype Notes: [Project Name]

## Initial Concept
[What user described initially]

## Core Interaction
[The main thing users do in the prototype]

## Tech Choices
- [Technology 1]: [Why we chose it]
- [Technology 2]: [Why we chose it]

## Learnings During Iteration

### [Date/Session 1]
- [Insight 1: what we learned from user feedback]
- [Insight 2: what worked well]
- [Insight 3: what didn't work]

### [Date/Session 2]
- [New learning 1]
- [New learning 2]

## Key Features User Wants
- [ ] [Feature 1 - confirmed important]
- [ ] [Feature 2 - mentioned multiple times]
- [ ] [Feature 3 - nice to have]

## Things to Avoid
- [Thing 1 user doesn't like]
- [Thing 2 that adds complexity without value]

## Open Questions
- [Question 1 to address in requirements phase]
- [Question 2 to address in requirements phase]

## Next Steps
[Ready for /clarify_requirements when prototype exploration is complete]
```

