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
- Use consistent colors with explicit Mermaid styling:
  - People: #08427B (dark blue), white text
  - Main system: #1168BD (blue), white text
  - External systems: #999999 (gray), white text
  - Containers: #438DD5 (light blue)
  - Components: #85BBF0 (very light blue)
  - Databases: #438DD5 with cylinder shape

**IMPORTANT: Apply styles using classDef and class in Mermaid. Example:**

    flowchart TB
        classDef person fill:#08427B,stroke:#073B6F,color:#FFFFFF
        classDef system fill:#1168BD,stroke:#0E5AA7,color:#FFFFFF
        classDef external fill:#999999,stroke:#8A8A8A,color:#FFFFFF
        classDef container fill:#438DD5,stroke:#3A7BBE,color:#FFFFFF
        classDef component fill:#85BBF0,stroke:#78A8D8,color:#000000
        classDef database fill:#438DD5,stroke:#3A7BBE,color:#FFFFFF

        User[User]
        System[My System]
        External[External System]
        
        class User person
        class System system
        class External external

**Legend must be visually distinguishable** - each element type must look different in the rendered diagram.

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

## Output Files

After executing this prompt:

| File | Location | Content |
|------|----------|---------|
| C4 Diagrams | `docs/C4-diagrams.md` | The generated diagrams |
| Prompt used | `docs/prompts/03-tdd-to-c4.md` | This prompt with your input (without the full TDD) |

**Note:** In the saved prompt, replace the full TDD content with `[See docs/TDD.md]` to avoid duplication.

---

## Tips

1. **Maintain consistency:** Use the same names from the TDD
2. **Don't overload:** A diagram with >15 elements is hard to read
3. **Data flow:** Show direction with clear arrows
4. **Context:** Each diagram should be understandable without reading the others
5. **Validate visually:** After generating, render the Mermaid diagrams and verify the legend matches the actual elements
6. **Own the document:** If styles don't render correctly, use `prompt-refinement.md` to fix specific diagrams
