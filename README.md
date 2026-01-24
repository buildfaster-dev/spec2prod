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

### Option A: Use the Full Kit

```bash
# Clone
git clone https://github.com/[your-username]/spec2prod.git
cd spec2prod

# Go to tutorial
open 04-guides/tutorial-first-session.md
```

### Option B: Just the Context for Claude Code

```bash
# Copy to your existing project
cp -r 03-ai-context/* your-project/
cd your-project
claude
```

### Option C: Start from Scratch

```bash
# 1. Copy only the prompts
cp -r 00-prompts/ my-new-project/

# 2. Write your idea and use prompt-idea-to-prd.md
# 3. Follow the transformation flow
```

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
│   └── prompt-to-adr.md           # Decision → ADR
│
├── 01-product/              # 📋 Product & Architecture
│   ├── PRD.md                     # Product Requirements
│   ├── TDD.md                     # Technical Design
│   ├── C4-diagrams.md             # Architecture diagrams
│   └── ADRs/                      # Decision Records
│       └── ADR-001-sqlite.md
│
├── 02-specs/                # 📝 Specifications
│   ├── api-spec.md                # CLI/API specification
│   ├── data-model.md              # Database schema
│   └── test-spec.md               # Test cases
│
├── 03-ai-context/           # 🤖 Context for Claude Code
│   ├── CLAUDE.md                  # Main context file
│   └── .claude/
│       └── commands/              # Custom slash commands
│           ├── implement.md
│           ├── test.md
│           └── fix.md
│
└── 04-guides/               # 📚 Documentation (Diátaxis)
    ├── tutorial-first-session.md  # Learn by doing
    ├── howto-recipes.md           # Specific tasks
    ├── reference-cheatsheet.md    # Quick reference
    └── explanation-pdd.md         # Understand PDD flow
```

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

**Minimum viable flow:** Idea → PRD → TDD → CLAUDE.md → Code

---

## 📖 How to Use the Prompts

Each prompt in `00-prompts/` transforms one document into another:

```bash
# 1. Open Claude (claude.ai or Claude Code)
# 2. Copy the prompt content
# 3. Replace [PASTE HERE] with your document
# 4. Execute
# 5. Save the result in the corresponding folder
```

**Example:**

```markdown
# Content from prompt-idea-to-prd.md
Act as a senior Product Manager...

## Idea
A task app with AI to decompose complex tasks...

## Context
- User: Developers learning AI Native
- Stack: Python + OpenAI SDK
...
```

---

## 🎓 Documentation (Diátaxis)

| Type | File | When to Use |
|------|------|-------------|
| **Tutorial** | `tutorial-first-session.md` | First time, want to learn by doing |
| **How-To** | `howto-recipes.md` | Have a specific task to solve |
| **Reference** | `reference-cheatsheet.md` | Need quick lookup |
| **Explanation** | `explanation-pdd.md` | Want to understand the full PDD flow |

---

## 🛠️ For Your Own Project

### Option A: Use as Template

```bash
# Copy the entire structure
cp -r spec2prod/ my-new-project/
cd my-new-project/

# Edit documents for your project
# Start with PRD.md
```

### Option B: Just the AI Context

```bash
# Copy only what Claude needs
cp -r 03-ai-context/* my-project/
```

### Option C: Just the Prompts

```bash
# Use prompts to generate docs from scratch
# Start with prompt-idea-to-prd.md
```

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

→ [View Full Roadmap](spec2prod/ROADMAP.md)

---

## 🤝 Contributing

Contributions welcome! See [CONTRIBUTING.md](spec2prod/CONTRIBUTING.md)

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
