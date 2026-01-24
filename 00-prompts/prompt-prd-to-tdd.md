# Prompt: PRD → Technical Design Document (TDD)

## When to Use
When you have an approved PRD and need to define the technical architecture and implementation decisions.

## Required Input
- Complete PRD
- Additional technical constraints (if any)
- Stack preferences (if any)

---

## Prompt

```markdown
Act as a Staff Engineer / Software Architect. Transform the following PRD into a Technical Design Document (TDD).

## PRD
[PASTE COMPLETE PRD HERE]

## Additional Constraints
- Preferred stack: [INDICATE]
- Development time: [INDICATE]
- Team experience: [INDICATE]
- Available infrastructure: [INDICATE]

## Instructions
Generate a TDD with the following sections:

### 1. Technical Overview
- System Purpose: Technical summary of the system
- Key Technical Decisions: Main architectural decisions with justification
- Tech Stack: Complete list with versions and justification for each choice

### 2. Architecture

#### 2.1 High-Level Architecture
- Architecture diagram (describe to generate with Mermaid)
- Main components and their responsibilities
- Main data flow

#### 2.2 Component Design
For each main component:
- Responsibility
- Interfaces (input/output)
- Dependencies
- Implementation considerations

### 3. Data Design

#### 3.1 Data Model
- Main entities with attributes
- Relationships between entities
- ER diagram (describe to generate with Mermaid)

#### 3.2 Storage Strategy
- Selected database and justification
- Indexing strategy
- Migration considerations

### 4. API Design
- Main endpoints
- Request/Response formats
- Error handling strategy
- Versioning (if applicable)

### 5. Integration Design

#### 5.1 External Services
For each external service:
- Service and purpose
- Integration method
- Error handling
- Rate limiting / retry strategy

### 6. Security Considerations
- Authentication/Authorization (if applicable)
- Data protection
- Input validation
- Secrets management

### 7. Testing Strategy
- Unit testing approach
- Integration testing approach
- Coverage targets
- Mocking strategy for external services

### 8. Implementation Plan
- Implementation phases
- Milestones
- Identified technical risks

### 9. ADRs (Architectural Decision Records)
For each important decision:
- Context
- Decision
- Consequences
- Alternatives considered

## Output Format
- Structured markdown
- Diagrams in Mermaid format
- Example code where it helps clarify
- Tables for comparisons and structured lists
```

---

## Usage Example

**Input:**
```
## PRD
AI-Powered ToDo App

Problem: Developers need a practical project to learn AI Native Development
Solution: Task manager with OpenAI integration for decomposition
User Stories: CRUD operations + AI decompose command
[... rest of PRD content ...]

## Additional Constraints
- Preferred stack: Python 3.11 + Typer + SQLModel + OpenAI SDK
- Development time: 4 weeks
- Team experience: 1 developer learning AI Native Development
- Available infrastructure: Local development only
```

**How to use:** Copy the Prompt section above, then replace `[PASTE COMPLETE PRD HERE]` with your PRD content and fill in the `[INDICATE]` placeholders with your constraints.

**Expected output:** A complete TDD with architecture diagrams, component design, data model, and implementation plan.

---

## Tips

1. **Be specific with the stack:** "Python" is not enough, specify "Python 3.11 + FastAPI 0.104"
2. **Document the "why":** Every technical decision should have justification
3. **Think about the future:** What happens if the scope grows?
4. **Identify risks:** Better to anticipate them than discover them during implementation
