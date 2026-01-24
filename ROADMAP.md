# spec2prod Roadmap

> From specification to production, in 3 stages

---

## Overview

```
┌─────────────────────────────────────────────────────────────────────────┐
│                                                                         │
│   STAGE 1              STAGE 2              STAGE 3                     │
│   AI Native    ───►    Agentic     ───►    Agent-Ready                  │
│   Development          Development          Development                 │
│                                                                         │
│   "AI as               "Autonomous          "Software designed          │
│    pair programmer"     agents"              for agents"                │
│                                                                         │
│   ✅ CURRENT           🔜 NEXT              🔮 FUTURE                   │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Stage 1: AI Native Development ✅

> **Status:** Current  
> **Focus:** Using AI as a tool during development

### Features

| Feature | Description | Status |
|---------|-------------|--------|
| Prompt Library | Document transformation | ✅ Done |
| PRD Template | Product Requirements | ✅ Done |
| TDD Template | Technical Design | ✅ Done |
| C4 Diagrams | Visual architecture | ✅ Done |
| API Spec | Interface specification | ✅ Done |
| Test Spec | Test cases | ✅ Done |
| CLAUDE.md | Context for Claude Code | ✅ Done |
| Slash Commands | /implement, /test, /fix | ✅ Done |
| Diátaxis Guides | Tutorial, How-To, Reference, Explanation | ✅ Done |

### Workflow

```
Human defines → AI generates → Human reviews → AI implements → Human validates
```

### How It's Used

1. You write the idea
2. You use prompts to generate documents
3. You review and adjust
4. Claude Code implements
5. You validate the result

---

## Stage 2: Agentic Development Kit 🔜

> **Status:** Next  
> **Focus:** Autonomous agents executing complex tasks

### Planned Features

| Feature | Description | Status |
|---------|-------------|--------|
| Multi-Agent Workflows | Multiple Claude instances in parallel | 🔜 Planned |
| Git Worktrees Setup | Configuration for parallel work | 🔜 Planned |
| Agent Orchestration | Coordinating specialized agents | 🔜 Planned |
| MCP Server Templates | Pre-configured MCP servers | 🔜 Planned |
| Autonomous Pipelines | CI/CD with agents | 🔜 Planned |
| Context Management | Strategies for long context | 🔜 Planned |
| Agent Memory | Persistence between sessions | 🔜 Planned |

### Workflow

```
Human defines goal → Agents plan → Agents execute in parallel → Agents validate → Human approves
```

### How It Will Be Used

1. You define the high-level objective
2. A "Planner" agent decomposes into tasks
3. Specialized agents execute in parallel:
   - Dev Agent: Implements code
   - Test Agent: Writes and runs tests
   - Review Agent: Reviews changes
   - Docs Agent: Updates documentation
4. Agents coordinate via handoffs
5. You approve the final result

### New Documents

```
05-agentic/
├── multi-agent-setup.md       # Configure multiple agents
├── worktree-workflow.md       # Git worktrees for parallelism
├── mcp-servers/               # MCP server templates
│   ├── playwright.md
│   ├── database.md
│   └── github.md
├── orchestration-patterns.md  # Coordination patterns
└── context-strategies.md      # Long context management
```

---

## Stage 3: Agent-Ready Development Kit 🔮

> **Status:** Future  
> **Focus:** Software designed from the start to be operated by agents

### Planned Features

| Feature | Description | Status |
|---------|-------------|--------|
| Agent-Optimized Specs | Specs in optimal format for LLMs | 🔮 Future |
| Semantic Documentation | Docs with metadata for agents | 🔮 Future |
| Self-Healing Pipelines | Pipelines that self-repair | 🔮 Future |
| Agent APIs | APIs designed for agent consumption | 🔮 Future |
| Feedback Loops | Continuous agent learning | 🔮 Future |
| Agent Observability | Monitoring agent behavior | 🔮 Future |

### Workflow

```
Human defines business goal → Agent system operates autonomously → Human monitors outcomes
```

### How It Will Be Used

1. You define business goals (not technical tasks)
2. Agent system:
   - Interprets the goal
   - Designs the solution
   - Implements
   - Tests
   - Deploys
   - Monitors
   - Iterates based on feedback
3. You monitor business metrics
4. You intervene only on significant deviations

### New Documents

```
06-agent-ready/
├── agent-optimized-specs/     # Specs in LLM-friendly format
│   ├── schema-spec.md
│   └── semantic-markers.md
├── self-healing/              # Self-repair patterns
├── agent-apis/                # API design for agents
├── feedback-systems/          # Learning loops
└── observability/             # Agent monitoring
```

---

## Evolution Criteria

### From Stage 1 to Stage 2

You're ready for Agentic when:

- [ ] You've mastered the complete AI Native flow
- [ ] You've completed at least 3 features with the kit
- [ ] You feel the bottleneck is your review speed, not the AI's
- [ ] You want to delegate complete tasks, not just code generation

### From Stage 2 to Stage 3

You're ready for Agent-Ready when:

- [ ] You have multiple agents working in parallel consistently
- [ ] Your specs are so clear that agents rarely ask for clarification
- [ ] 80%+ of generated code passes review without changes
- [ ] You want the system to operate with minimal intervention

---

## Contributing to the Roadmap

Have ideas for Stage 2 or 3 features?

1. Open an issue with the `roadmap` label
2. Describe the feature and which stage it fits
3. Explain the problem it solves

---

## Estimated Timeline

| Stage | Target | Dependencies |
|-------|--------|--------------|
| 1 - AI Native | ✅ Now | - |
| 2 - Agentic | Q2 2025 | Claude Code improvements, MCP maturity |
| 3 - Agent-Ready | Q4 2025 | Established agentic patterns |

*Timeline subject to change based on ecosystem evolution*

---

*This document will be updated as we progress through the stages*
