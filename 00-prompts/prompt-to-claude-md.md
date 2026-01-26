# Prompt: All Docs → CLAUDE.md

## When to Use
When you have all project documentation (PRD, TDD, C4, Specs) and need to generate the CLAUDE.md file that will serve as the main context for Claude Code.

## Required Input
- Complete PRD
- Complete TDD
- API Spec
- Data Model
- Any relevant ADRs

---

## Prompt

```markdown
Act as an expert in AI Native Development and Claude Code. Generate an optimized CLAUDE.md file to serve as the project's main context.

IMPORTANT: This is a new conversation. Do not use any context from previous chats. Only use the information explicitly provided in this prompt.

## Project Documentation
[PASTE OR REFERENCE ALL DOCS]

## Instructions

The CLAUDE.md should be **concise but complete**. Claude Code will read it at the start of each session to understand the project.

### Required Structure

#### 1. Project Overview (3-5 lines)
- What the project is
- Main stack
- Current status (MVP, in development, etc.)

#### 2. Architecture Summary
- Simple ASCII diagram of components
- Main data flow
- External services

#### 3. Directory Structure
- Directory tree with description of each folder
- Key files and their purpose

#### 4. Key Files
- List of most important files
- What each contains
- When to modify them

#### 5. Development Commands
- How to run the project
- How to run tests
- How to lint/format

#### 6. Code Conventions
- Naming conventions
- Patterns used
- Things to avoid

#### 7. Current Tasks / TODOs
- What's in progress
- Next steps
- Known blockers

#### 8. Common Patterns
- Code examples for common tasks
- How to add a new command
- How to add a new test

### Writing Principles

1. **Brevity:** Claude has context limits. Every word must add value.
2. **Actionable:** Information that helps write code, not theory.
3. **Up-to-date:** Must reflect the actual state of the code.
4. **Examples > Explanations:** Showing code is better than describing it.

### Output Format
- Markdown
- Maximum 500 lines (ideal: 200-300)
- Inline code for short examples
- File references for long examples
```

---

## Usage Example

**Input:**
```
## Project Documentation

### PRD.md
AI-Powered ToDo App - User stories, requirements
[... PRD content or reference ...]

### TDD.md
Architecture, components, data model
[... TDD content or reference ...]

### api-spec.md
CLI commands: add, list, show, complete, delete, decompose
[... API spec content or reference ...]

### data-model.md
Task entity with fields and relationships
[... data model content or reference ...]

### test-spec.md
Test cases and coverage targets
[... test spec content or reference ...]
```

**How to use:** Copy the Prompt section above, then replace `[PASTE OR REFERENCE ALL DOCS]` with your project documentation. You can either paste the full content or provide file references if using Claude Code.

**Expected output:** A concise CLAUDE.md (200-300 lines) with project overview, ASCII architecture, directory structure, commands, and code patterns.

---

## Output Files

After executing this prompt:

| File | Location | Content |
|------|----------|---------|
| CLAUDE.md | `CLAUDE.md` (root) | The generated AI context file |
| Prompt used | `docs/prompts/06-to-claude-md.md` | This prompt with your input |

**Note:** CLAUDE.md must be at the project root for Claude Code to read it automatically.

---

## Tips

1. **Less is more:** A 100-line useful CLAUDE.md > 500 lines of filler
2. **Update frequently:** CLAUDE.md should evolve with the code
3. **Test with Claude:** Ask "what does this project do?" and validate the answer
4. **Include anti-patterns:** What NOT to do is as useful as what to do
5. **Own the document:** If the generated CLAUDE.md doesn't capture your project well, use `prompt-refinement.md` to adjust

