# Tutorial 05: UI Components

> ⏱️ Time: 25 minutes  
> 📋 Outcome: HTML card generators for task display in ChatGPT

---

## Prerequisites

- Completed [tutorial-04-tools.md](./tutorial-04-tools.md)
- Claude Code running in your project directory

---

## Objective

Create `ui/components.py` with pure functions that generate HTML for inline cards.

**Result:** Functions that render tasks as HTML cards for display in ChatGPT.

---

## Step 1: Implement UI Components

In Claude Code:

```
Implement src/ui/components.py according to docs/TDD.md section 2.2.4 (UI Components)
```

Claude will:
1. Read your TDD.md
2. Create render functions for task cards
3. Generate HTML following Apps SDK guidelines

Select `Yes` when prompted.

**TDD specifies these functions (section 2.2.4):**

```python
def render_task_card(task: Task) -> str
def render_task_list(tasks: list[Task]) -> str
def render_confirmation(message: str, task: Task | None = None) -> str
def render_task_hierarchy(parent: Task, subtasks: list[Task]) -> str
```

---

## Step 2: Review the Changes

In a separate terminal:

```bash
git diff src/ui/components.py
```

**What to look for:**

| Function | Check |
|----------|-------|
| `render_task_card` | Shows title, status, created date |
| `render_task_list` | Renders multiple tasks |
| `render_confirmation` | Success/delete messages |
| `render_task_hierarchy` | Parent with subtasks |

These are pure functions (no dependencies) that return HTML strings.

---

## Step 3: Test UI Components

```
Create tests for the UI components
```

Claude will create a test file (e.g. `tests/unit/test_components.py` or `tests/unit/test_ui.py`).

### What might happen

**Tests check HTML output**

Tests will verify that rendered HTML contains expected elements like task titles and HTML tags.

---

## Step 4: Commit

```
commit this
```

Then push:

```
push it
```

---

## Step 5: Update CLAUDE.md

```
Update CLAUDE.md: mark "UI layer" as complete in Implementation Order
```

---

## Done! ✅

**What you learned:**
- UI components are pure functions (no side effects)
- HTML inline cards for ChatGPT display
- Separation of UI from business logic

---

## Common Issues

### Import error: Task model not found

```
The UI components need to import Task from schemas. Fix the import path.
```

### HTML not rendering in ChatGPT

The HTML will only render when connected to ChatGPT via MCP. For now, tests verify the HTML structure.

### Stubs from tutorial-04 need replacement

If you created stubs in tutorial-04:

```
Replace the stub functions in ui/components.py with full implementations
```

---

## Next

Continue with [tutorial-06-server.md](./tutorial-06-server.md)
