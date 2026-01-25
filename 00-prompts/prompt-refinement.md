# Prompt: Document Refinement

## When to Use
When you need to modify a specific section of an existing document (PRD, TDD, API Spec, etc.) without risking changes to other sections.

## Required Input
- The complete current document
- Section name to modify
- Description of required changes

---

## Prompt

```markdown
Modify ONLY the specified section of this document. Keep everything else EXACTLY as is, including all other sections, formatting, tables, and content.

IMPORTANT: This is a new conversation. Do not use any context from previous chats. Only use the information explicitly provided in this prompt.

## Document Type
[PRD | TDD | API Spec | Test Spec | C4 Diagrams | Other]

## Current Document
[PASTE COMPLETE DOCUMENT HERE]

## Section to Modify
[SECTION NAME OR NUMBER, e.g., "6.2 Project Structure" or "User Stories"]

## Required Changes
[DESCRIBE WHAT YOU WANT DIFFERENT]

## Output
Return the COMPLETE document with ONLY the specified section modified. Do not change anything else.
```

---

## Usage Example

**Input:**
```markdown
## Document Type
PRD

## Current Document
# Product Requirements Document (PRD)
## ChatGPT ToDo App with AI Task Decomposition
...
## 6. Architecture
### 6.1 System Overview
...
### 6.2 Project Structure
    chatgpt-todo-app/
    ├── README.md
    ├── requirements.txt
    ├── pyproject.toml
    ├── src/
    │   ├── __init__.py
    │   ├── server.py
    │   ├── tools/
    │   ├── database/
    │   └── ui/
    └── tests/
...

## Section to Modify
6.2 Project Structure

## Required Changes
Update to this structure:
    chatgpt-todo-app/
    ├── docs/
    │   ├── prompts/              # Prompts used (traceability)
    │   │   ├── 01-idea-to-prd.md
    │   │   └── 02-prd-to-tdd.md
    │   ├── ADRs/                 # Architectural Decision Records
    │   │   └── ADR-001-xxx.md
    │   ├── PRD.md                # Generated outputs
    │   ├── TDD.md
    │   └── C4-diagrams.md
    ├── src/                      # Keep existing structure
    │   ├── __init__.py
    │   ├── server.py
    │   ├── tools/
    │   ├── database/
    │   └── ui/
    ├── tests/
    ├── CLAUDE.md                 # AI context (root level)
    ├── README.md
    ├── requirements.txt
    └── pyproject.toml

## Output
Return the COMPLETE document with ONLY the specified section modified. Do not change anything else.
```

**How to use:** Copy the Prompt section above, then:
1. Specify the document type
2. Paste your complete current document
3. Identify the exact section to modify
4. Describe the changes clearly

**Expected output:** The complete document with only the specified section changed.

---

## Tips

1. **Be specific about the section** - Use section numbers or exact headings
2. **Describe changes clearly** - "Add X", "Remove Y", "Change Z to W"
3. **Verify the output** - Diff the result against original to confirm only intended changes
4. **For multiple sections** - Run the prompt multiple times, one section at a time
5. **Keep a backup** - Commit your document before applying refinements

---

## When NOT to Use

| Scenario | Better Approach |
|----------|-----------------|
| Typos, small formatting fixes | Edit manually |
| Changing 3+ sections | Re-generate with updated input |
| Structural document changes | Re-generate from scratch |
| Adding a single line | Edit manually |

---

## Naming Convention

When saving refinement prompts to your project's `docs/prompts/`:

```
docs/prompts/
├── 01-idea-to-prd.md              # Initial generation
├── 01a-prd-refine-structure.md    # First refinement
├── 01b-prd-refine-stories.md      # Second refinement
├── 02-prd-to-tdd.md               # Next transformation
└── ...
```

Use letter suffixes (a, b, c) for refinements to the same document.
