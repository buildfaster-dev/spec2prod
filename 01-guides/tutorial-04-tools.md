# Tutorial 04: Tools Layer

> ⏱️ Time: 45 minutes  
> 📋 Outcome: MCP tools with Pydantic schemas for all CRUD operations

---

## Prerequisites

- Completed [tutorial-03-database.md](./tutorial-03-database.md)
- Claude Code running in your project directory

---

## Objective

Create the tools layer with:
- `schemas.py` - Pydantic models for tool inputs/outputs
- `task_tools.py` - Tool handlers that coordinate database and UI

**Result:** All MCP tools defined and ready to register with the server.

---

## Part A: Schemas

### Step 1: Implement Schemas

In Claude Code:

```
Implement src/tools/schemas.py with Pydantic models according to docs/TDD.md section 3.1 (Pydantic Models)
```

Claude will:
1. Read your TDD.md
2. Create Pydantic models: TaskBase, TaskCreate, Task
3. Add tool input schemas: AddTaskInput, ListTasksInput, etc.
4. Add error handling models

Select `Yes` when prompted.

---

### Step 2: Review Schemas

In a separate terminal:

```bash
git diff src/tools/schemas.py
```

**What to look for:**

| Model | Fields |
|-------|--------|
| `TaskBase` | title with validation |
| `TaskCreate` | title + optional parent_id |
| `Task` | id, title, completed, created_at, parent_id, subtasks |
| `AddTaskInput` | title, optional parent_id |
| `ListTasksInput` | filter, optional parent_id |
| `CompleteTaskInput` | task_id |
| `DeleteTaskInput` | task_id |
| `DecomposeTaskInput` | task_id, subtask_titles |

---

### Step 3: Test Schemas

Claude may suggest adding tests. Accept, or ask:

```
Create tests for the schemas
```

Claude will create `tests/unit/test_schemas.py` and run them.

---

### Step 4: Commit Schemas

```
commit this
```

Then push:

```
push it
```

---

## Part B: Tool Handlers

### Step 5: Implement Tool Handlers

```
Implement src/tools/task_tools.py with all tool handlers according to docs/TDD.md section 2.2.2
```

Claude will create handlers for:
- `add_task` - Create a new task
- `list_tasks` - List tasks with optional filter
- `complete_task` - Toggle task completion
- `delete_task` - Remove a task
- `decompose_task` - Create subtasks (AI feature)

---

### Step 6: Review Tool Handlers

```bash
git diff src/tools/task_tools.py
```

**What to look for:**

| Tool | Input | Output |
|------|-------|--------|
| `add_task` | `{title: str, parent_id?: int}` | Task + inline card |
| `list_tasks` | `{filter?: str, parent_id?: int}` | Tasks + list card |
| `complete_task` | `{task_id: int}` | Task + confirmation |
| `delete_task` | `{task_id: int}` | Confirmation |
| `decompose_task` | `{task_id: int, count?: int}` | Subtasks + hierarchy card |

---

### Step 7: Test Tool Handlers

```
Create tests for the tool handlers
```

### What might happen

**Tests need database fixtures**

The tools depend on the database layer. Claude should reuse or extend the database fixtures:

```python
@pytest.fixture
async def repo(test_db):
    return TaskRepository(test_db)
```

---

**UI components not implemented yet**

If task_tools.py imports from ui/components.py which doesn't exist:

```
The tools are importing ui/components.py but it doesn't exist yet. Create a stub or skip UI generation for now.
```

---

### Step 8: Commit Tool Handlers

```
commit this
```

Then push:

```
push it
```

---

## Step 9: Update CLAUDE.md

```
Update CLAUDE.md: mark "Tools layer" as complete in Implementation Order
```

---

## Done! ✅

**What you learned:**
- Pydantic models for input validation and serialization
- Implement and test each component before moving to the next
- Tool handlers coordinate between layers
- Each tool returns data (for AI) + UI (for user)
- decompose_task relies on ChatGPT to generate subtasks

---

## Common Issues

### Circular imports

If schemas imports from models or vice versa:

```
Restructure to avoid circular imports - schemas should be independent
```

### UI components not ready

If tools try to import UI components:

```
Create stub functions in ui/components.py that return empty strings for now
```

### Async/await issues

All tool handlers should be async:

```
The tool handlers need to be async to work with the async database layer
```

### MCP decorator not found

If Claude tries to use MCP decorators:

```
Don't add MCP decorators yet - we'll register tools in server.py later
```

---

## Next

Continue with [tutorial-05-ui.md](./tutorial-05-ui.md)
