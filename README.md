# spec2prod

> From specification to production. A framework for building software with AI.

**Stage 1 of 3** | [View Roadmap →](./ROADMAP.md)

```
Stage 1: AI Native ✅  →  Stage 2: Agentic 🔜  →  Stage 3: Agent-Ready 🔮
         (current)            (next)                 (future)
```

---

## 🎯 What is This

A complete set of documents that allow you to:

1. **Define** your product (PRD → TDD → C4 → Specs)
2. **Transform** documents automatically with reusable prompts
3. **Build** with Claude Code using structured context
4. **Learn** following the Diátaxis framework

---

## 🚀 Quick Start

### Option A: Start a New Project

```bash
# Clone spec2prod
git clone https://github.com/[your-username]/spec2prod.git

# Copy prompts to your project
cp -r spec2prod/00-prompts/ my-new-project/docs/

# Follow the transformation flow
# Start with prompt-idea-to-prd.md
```

### Option B: Learn First

```bash
# Clone and read the tutorial
git clone https://github.com/[your-username]/spec2prod.git
cd spec2prod

# Go to tutorial
open 01-guides/tutorial-claude-code-setup.md
```

### Option C: See a Real Example

Check [chatgpt-todo-app](https://github.com/jyr-at-bft/chatgpt-todo-app) - a complete project built using spec2prod.

---

## 📁 Structure

```
.
├── 00-prompts/              # 🔄 Transformation prompts
│   ├── prompt-idea-to-prd.md      # Idea → PRD
│   ├── prompt-prd-to-tdd.md       # PRD → TDD
│   ├── prompt-tdd-to-c4.md        # TDD → C4 Diagrams
│   ├── prompt-to-api-spec.md      # TDD → API Spec
│   ├── prompt-to-test-spec.md     # PRD+TDD → Test Spec
│   ├── prompt-to-claude-md.md     # All → CLAUDE.md
│   ├── prompt-to-adr.md           # Decision → ADR
│   └── prompt-refinement.md       # 🔧 Modify specific sections
│
└── 01-guides/               # 📚 Documentation (Diátaxis)
    ├── tutorial-claude-code-setup.md  # Learn by doing
    ├── howto-recipes.md           # Specific tasks
    ├── reference-cheatsheet.md    # Quick reference
    └── explanation-pdd.md         # Understand PDD flow
```

**Real-world example:** [chatgpt-todo-app](https://github.com/jyr-at-bft/chatgpt-todo-app) - A complete project built using spec2prod prompts.

---

## 🔄 Transformation Flow

```
Idea ──► PRD ──► TDD ──► C4 ──► Specs ──► CLAUDE.md ──► Claude Code ──► Code
     ↑       ↑       ↑       ↑        ↑
     │       │       │       │        │
     │       │       │       │        └── prompt-to-claude-md.md
     │       │       │       │
     │       │       │       ├── prompt-to-api-spec.md
     │       │       │       └── prompt-to-test-spec.md
     │       │       │
     │       │       └── prompt-tdd-to-c4.md
     │       │
     │       └── prompt-prd-to-tdd.md
     │
     └── prompt-idea-to-prd.md
```

### Transformation Table

| # | Transition | Prompt | Output | Required |
|---|------------|--------|--------|----------|
| 1 | Idea → PRD | `prompt-idea-to-prd.md` | Product Requirements Document | ✅ Yes |
| 2 | PRD → TDD | `prompt-prd-to-tdd.md` | Technical Design Document | ✅ Yes |
| 3 | TDD → C4 | `prompt-tdd-to-c4.md` | Architecture Diagrams | ⚪ Optional |
| 4 | TDD → API Spec | `prompt-to-api-spec.md` | API/CLI Specification | ⚪ Optional |
| 5 | PRD+TDD → Tests | `prompt-to-test-spec.md` | Test Specification | ⚪ Optional |
| 6 | All → Context | `prompt-to-claude-md.md` | CLAUDE.md for Claude Code | ✅ Yes |
| 7 | Decision → ADR | `prompt-to-adr.md` | Architectural Decision Record | ⚪ Optional |
| 🔧 | Doc → Doc | `prompt-refinement.md` | Modified Document | Utility |

**Minimum viable flow:** Idea → PRD → TDD → CLAUDE.md → Code

---

## 📖 How to Use the Prompts

Each prompt in `00-prompts/` transforms one document into another:

```bash
# 1. Open a NEW conversation in Claude (to avoid context bleeding)
# 2. Copy the Prompt section (inside the ```markdown``` block)
# 3. Replace [PLACEHOLDERS] with your content
# 4. Execute
# 5. Save the output in docs/ (e.g., docs/PRD.md)
# 6. Save the prompt used in docs/prompts/ (for traceability)
```

**Important:**
- Use a **new conversation** for each prompt to prevent prior context from affecting the output
- In saved prompts, replace full document content with `[See docs/PRD.md]` to avoid duplication

**Example:**

```markdown
# Content from prompt-idea-to-prd.md
Act as a senior Product Manager...

## Idea
A task app with AI to decompose complex tasks...

## Additional Context
- Target user: Developers learning AI Native
- Preferred tech stack: Python + OpenAI SDK
...
```

---

## 📁 Recommended Project Structure

When using spec2prod for your project, keep all documentation **inside your project repository**:

```
your-project/
├── docs/
│   ├── prompts/              # Prompts used (traceability)
│   │   ├── 01-idea-to-prd.md
│   │   ├── 02-prd-to-tdd.md
│   │   └── ...
│   ├── ADRs/                 # Architectural Decision Records
│   │   └── ADR-001-xxx.md
│   ├── PRD.md                # Generated outputs
│   ├── TDD.md
│   └── C4-diagrams.md
├── src/                      # Source code
├── tests/                    # Tests
├── CLAUDE.md                 # AI context (root level)
└── README.md
```

**Why inside the same repo?**

- CLAUDE.md must be at the root for Claude Code to read it
- Docs and code evolve together (single git history)
- One `git clone` = everything needed
- Documentation describes the software being built

---

## 🎓 Documentation (Diátaxis)

| Type | File | When to Use |
|------|------|-------------|
| **Tutorial** | `tutorial-claude-code-setup.md` | First time, want to learn by doing |
| **How-To** | `howto-recipes.md` | Have a specific task to solve |
| **Reference** | `reference-cheatsheet.md` | Need quick lookup |
| **Explanation** | `explanation-pdd.md` | Want to understand the full PDD flow |

---

## 🛠️ For Your Own Project

### Option A: Use the Prompts

```bash
# Copy prompts to your project
cp -r spec2prod/00-prompts/ my-project/docs/prompts/

# Start with prompt-idea-to-prd.md
# Follow the transformation flow
```

### Option B: Follow the Tutorial

```bash
# Read the tutorial first
open spec2prod/01-guides/tutorial-claude-code-setup.md

# Then apply to your project
```

### Option C: See a Real Example

Study [chatgpt-todo-app](https://github.com/jyr-at-bft/chatgpt-todo-app) to see how a complete project uses spec2prod.

---

## ✅ Checklist: AI Native Ready Project

- [ ] PRD with user stories and acceptance criteria
- [ ] TDD with architecture and technical decisions
- [ ] C4 diagrams (at least level 2)
- [ ] API Spec with examples
- [ ] Data Model with validations
- [ ] Test Spec with test cases
- [ ] CLAUDE.md up to date
- [ ] Slash commands for common tasks

---

## 🤔 FAQ

**Why so much documentation before coding?**

Because AI works better with context. 30 min of PRD saves hours of rework.

**Do I have to use all documents?**

No. The minimum viable is: PRD + CLAUDE.md. The rest adds precision.

**How do I keep docs updated?**

CLAUDE.md should be updated with every significant change. The rest are more stable.

**Does this replace traditional documentation?**

No, it complements it. These docs are for AI; user documentation is different.

---

## 📚 Resources

- [Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices)
- [Diátaxis Framework](https://diataxis.fr/)
- [C4 Model](https://c4model.com/)

---

## 🗺️ Roadmap

This kit evolves in 3 stages:

| Stage | Name | Status | Description |
|-------|------|--------|-------------|
| 1 | AI Native | ✅ Current | AI as pair programmer |
| 2 | Agentic | 🔜 Next | Autonomous agents in parallel |
| 3 | Agent-Ready | 🔮 Future | Software designed for agents |

→ [View Full Roadmap](./ROADMAP.md)

---

## 🤝 Contributing

Contributions welcome! See [CONTRIBUTING.md](./CONTRIBUTING.md)

Areas where you can help:
- 🟢 Improve existing documentation
- 🟢 Add examples
- 🟡 Create new prompts
- 🔴 Features for Stage 2 (Agentic)

---

## 📄 License

MIT License - see [LICENSE](./LICENSE)

---

## ⭐ Acknowledgments

- Anthropic for Claude Code
- The AI Native Dev community
- Diátaxis for the documentation framework

---

*Created to learn specification-driven development. January 2025.*

**Found it useful? ⭐ Star the repo!**


