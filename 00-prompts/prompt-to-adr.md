# Prompt: Technical Decision → ADR

## When to Use
When you need to document an important technical decision (database, framework, architecture, etc.)

## Required Input
- The decision made
- Options considered
- Project context

---

## Prompt

```markdown
Act as a Software Architect. Generate an ADR (Architectural Decision Record) for the following technical decision.

IMPORTANT: This is a new conversation. Do not use any context from previous chats. Only use the information explicitly provided in this prompt.

## Decision
[DESCRIBE THE DECISION]

## Options Considered
[LIST ALTERNATIVES]

## Project Context
[BRIEFLY DESCRIBE THE PROJECT AND ITS CONSTRAINTS]

## Instructions

Generate an ADR with the following sections:

### 1. Header
- Descriptive title (ADR-XXX: Verb + Decision)
- Status: Proposed | Accepted | Deprecated | Superseded
- Date
- Deciders

### 2. Context
- What problem we're solving
- Why this decision needs to be made now
- Relevant constraints

### 3. Decision
- The decision made in one clear sentence
- "We will use X for Y"

### 4. Rationale
For each option:
- Pros (✅)
- Cons (❌)
- Why yes or why not

### 5. Consequences
- Positive: What we gain
- Negative: What we lose or what trade-offs we accept
- Risks: What can go wrong and how we mitigate

### 6. Alternatives Considered
- Reference to Rationale section or summarized list

## Format
- Markdown
- Concise but complete
- Easy to scan (bullets, tables)
- Name file: ADR-XXX-keyword.md
```

---

## Usage Example

**Input:**
```
## Decision
Use SQLite as the database for the ToDo App

## Options Considered
1. SQLite - Embedded database, zero configuration
2. PostgreSQL - Full relational database, requires setup
3. JSON file - Flat file storage, no SQL support

## Project Context
Learning project for AI Native Development. Single user, needs data 
persistence, want easy setup for new developers. Timeline is 4 weeks.
```

**How to use:** Copy the Prompt section above, then replace `[DESCRIBE THE DECISION]` with your decision, `[LIST ALTERNATIVES]` with options you considered, and `[BRIEFLY DESCRIBE THE PROJECT AND ITS CONSTRAINTS]` with your context.

**Expected output:** Complete ADR with context, decision statement, pros/cons for each option, consequences, and risks.

---

## Output Files

After executing this prompt:

| File | Location | Content |
|------|----------|---------|
| ADR | `docs/ADRs/ADR-XXX-keyword.md` | The generated ADR |
| Prompt used | `docs/prompts/07-to-adr-XXX.md` | This prompt with your input |

**Naming convention:** Number ADRs sequentially (ADR-001, ADR-002) with a keyword describing the decision.

---

## Tips

1. **One decision = one ADR:** Don't mix multiple decisions
2. **Be honest with trade-offs:** ADRs are for future you
3. **Include the "why not":** As important as the "why yes"
4. **Update the status:** If a decision changes, don't delete, mark as superseded
5. **Own the document:** If the generated ADR doesn't capture your reasoning, use `prompt-refinement.md` to adjust

