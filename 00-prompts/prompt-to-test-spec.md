# Prompt: PRD + TDD → Test Specification

## When to Use
When you have PRD and TDD defined and need to generate test specifications before implementing (Test-Driven approach).

## Required Input
- PRD with user stories and acceptance criteria
- TDD with technical design
- Project scope (learning, MVP, production)

---

## Prompt

```markdown
Act as a senior QA Engineer / SDET. Generate a practical test specification based on the following documents.

IMPORTANT: This is a new conversation. Do not use any context from previous chats. Only use the information explicitly provided in this prompt.

## PRD
[PASTE PRD HERE]

## TDD
[PASTE TDD HERE]

## Project Scope
- Type: [Learning project | MVP | Production]
- Timeline: [INDICATE]
- Team size: [INDICATE]

## Instructions

Generate a CONCISE test specification. Focus on practical tests that can be implemented within the project timeline. Avoid over-engineering.

### 1. Test Strategy Overview
- Testing pyramid (unit > integration > e2e)
- Coverage target (single number, e.g., "70%")
- Tools and frameworks (only essential ones)

### 2. Unit Tests Specification
For each main component, list 3-5 critical test cases:
- 1-2 happy path
- 1-2 error cases
- 1 edge case (if relevant)

Format:
| ID | Description | Input | Expected |
|----|-------------|-------|----------|

### 3. Integration Tests Specification
List 5-10 integration tests covering the main flows. Focus on happy paths.

### 4. Fixtures
Simple fixtures needed for tests. No factory libraries for learning projects.

### 5. Test Cases per User Story
For each P0 user story: 2-3 test cases that verify acceptance criteria.

## Output Guidelines
- Keep document under 300 lines
- Prefer tables over prose
- Include 1-2 code examples for reference
- Skip E2E tests for learning projects
- Skip CI/CD configuration
```

---

## Usage Example

**Input:**
```
## PRD
ChatGPT ToDo App

User Stories: US-01 to US-07 (CRUD + AI decompose)
Acceptance criteria defined for each story
[... rest of PRD content ...]

## TDD
Components: Tools Layer, Database Layer, UI Components
External: ChatGPT via MCP Protocol
[... rest of TDD content ...]

## Project Scope
- Type: Learning project
- Timeline: 4 weeks
- Team size: 1 developer
```

**How to use:** Copy the Prompt section above, then replace `[PASTE PRD HERE]` with your PRD, `[PASTE TDD HERE]` with your TDD, and fill in the Project Scope.

**Expected output:** Concise test specification (~200-300 lines) with ~30 test cases covering critical paths.

---

## Output Files

After executing this prompt:

| File | Location | Content |
|------|----------|---------|
| Test Spec | `docs/test-spec.md` | The generated test specification |
| Prompt used | `docs/prompts/05-to-test-spec.md` | This prompt with your input (without full docs) |

**Note:** In the saved prompt, replace full document content with `[See docs/PRD.md]` and `[See docs/TDD.md]` to avoid duplication.

---

## Tips

1. **Start with happy paths:** Ensure it works before looking for bugs
2. **One test = one thing:** Each test verifies a single behavior
3. **Descriptive names:** `test_create_task_with_valid_title_returns_task_with_id`
4. **Consider maintenance:** Fragile tests are worse than no tests
5. **Match project scope:** A learning project needs ~30 tests, not 100+
6. **Own the document:** If the generated spec is too verbose, use `prompt-refinement.md` to simplify
