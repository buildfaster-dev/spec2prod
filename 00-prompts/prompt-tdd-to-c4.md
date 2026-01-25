# Prompt: TDD → C4 Model

## When to Use
When you have a TDD and need to generate architecture diagrams following the C4 model (Context, Container, Component, Code).

## Required Input
- Complete Technical Design Document
- Desired level of detail (C1, C2, C3, C4)

---

## Prompt

```markdown
Act as a Software Architect specialized in visual documentation. Generate C4 Model diagrams based on the following Technical Design Document.

IMPORTANT: This is a new conversation. Do not use any context from previous chats. Only use the information explicitly provided in this prompt.

## TDD
[PASTE COMPLETE TDD HERE]

## Required Levels
- [x] C1 - System Context
- [x] C2 - Container
- [x] C3 - Component (for: [SPECIFY CONTAINERS])
- [ ] C4 - Code (optional)

## Instructions

### For each level, generate:

#### C1 - System Context Diagram
- Main system in the center
- External actors (users, systems)
- High-level relationships
- Format: Mermaid flowchart

#### C2 - Container Diagram
- System containers (applications, databases, etc.)
- Technology of each container
- Communication between containers
- Format: Mermaid flowchart

#### C3 - Component Diagram
- Components within each specified container
- Responsibilities
- Dependencies between components
- Format: Mermaid flowchart

### C4 Conventions
- Use consistent colors:
  - People: #08427B (dark blue)
  - Main system: #1168BD (blue)
  - External systems: #999999 (gray)
  - Containers: #438DD5 (light blue)
  - Components: #85BBF0 (very light blue)
  - Databases: #438DD5 with cylinder

### For each diagram include:
1. Descriptive title
2. Legend if there are many elements
3. 2-3 line text description explaining the diagram

## Output Format
- Diagrams in Mermaid syntax
- Text description per diagram
- Notes on representation decisions
```

---

## Usage Example

**Input:**
```
## TDD
AI-Powered ToDo App

Architecture: Modular monolith (CLI → Services → Repository → SQLite)
Components: TaskService, AIService, TaskRepository
External: OpenAI API
[... rest of TDD content ...]

## Required Levels
- [x] C1 - System Context
- [x] C2 - Container
- [x] C3 - Component (for: Application Core)
- [ ] C4 - Code (optional)
```

**How to use:** Copy the Prompt section above, then replace `[PASTE COMPLETE TDD HERE]` with your TDD content and check the required levels (C1, C2, C3, C4). Specify which containers need C3 diagrams in `[SPECIFY CONTAINERS]`.

**Expected output:** Three Mermaid diagrams (System Context, Container, Component) with descriptions and consistent styling.

---

## Tips

1. **Maintain consistency:** Use the same names from the TDD
2. **Don't overload:** A diagram with >15 elements is hard to read
3. **Data flow:** Show direction with clear arrows
4. **Context:** Each diagram should be understandable without reading the others
