# Prompt: Idea → PRD

## When to Use
When you have a product/feature idea and need to convert it into a structured PRD.

## Required Input
- Idea description (can be informal)
- Target user context
- Known constraints (time, tech stack, etc.)

---

## Prompt

```markdown
Act as a senior Product Manager. Transform the following idea into a structured PRD (Product Requirements Document).

IMPORTANT: This is a new conversation. Do not use any context from previous chats. Only use the information explicitly provided in this prompt.

## Idea
[PASTE IDEA HERE]

## Additional Context
- Target user: [DESCRIBE]
- Preferred tech stack: [LIST]
- Estimated timeline: [INDICATE]
- Constraints: [LIST]

## Instructions
Generate a PRD with the following sections:

### 1. Overview
- Problem Statement: The specific problem we're solving
- Proposed Solution: High-level description of the solution
- Goals & Success Metrics: Measurable success metrics

### 2. User Personas
- Primary persona with characteristics, pain points, and goals
- Main jobs-to-be-done (JTBD)

### 3. User Stories
Format: "As a [persona], I want [action] so that [benefit]"
- Include acceptance criteria for each story
- Prioritize with MoSCoW (Must/Should/Could/Won't)

### 4. Functional Requirements
- Core features (MVP)
- Future features (post-MVP)
- Explicit out of scope

### 5. Non-Functional Requirements
- Performance expectations
- Security requirements
- Scalability considerations

### 6. Assumptions & Dependencies
- Assumptions we're making
- External dependencies

### 7. Open Questions
- Unresolved questions that need decision

## Output Format
- Structured markdown
- User stories in table format
- Priorities clearly marked
```

---

## Usage Example

**Input:**
```
## Idea
A ToDo app that uses AI to suggest how to break down large tasks into more manageable subtasks.

## Additional Context
- Target user: Developers who want to learn AI Native Development
- Preferred tech stack: Python + OpenAI SDK
- Estimated timeline: 4 weeks
- Constraints: Learning project, not production
```

**How to use:** Copy the Prompt section above, then replace `[PASTE IDEA HERE]` with your idea and fill in the `[DESCRIBE]`, `[LIST]`, `[INDICATE]` placeholders with your context.

**Expected output:** A complete PRD following the defined structure.

---

## Output Files

After executing this prompt:

| File | Location | Content |
|------|----------|---------|
| PRD | `docs/PRD.md` | The generated PRD |
| Prompt used | `docs/prompts/01-idea-to-prd.md` | This prompt with your input (without the full PRD) |

**Note:** In the saved prompt, replace the full PRD content with `[See docs/PRD.md]` to avoid duplication.

---

## Tips
1. The more context you provide in the input, the better the PRD
2. Iterate: generate a first version and then refine specific sections
3. Validate user stories with: "Is this testable?"
4. The generated PRD may include detailed NFRs (Non-Functional Requirements). For learning projects, consider simplifying with `prompt-refinement.md`
5. If something in the output doesn't make sense or you didn't ask for it, refine or remove it—you own the document
