# Tutorial 03: Database Layer

> ⏱️ Time: 30 minutes  
> 📋 Outcome: SQLite database with connection management and Task model

---

## Prerequisites

- Completed [tutorial-02-configuration.md](./tutorial-02-configuration.md)
- Claude Code running in your project directory

---

## Objective

Create the database layer with:
- `connection.py` - SQLite connection management with aiosqlite
- `models.py` - TaskRepository with CRUD operations

**Result:** You can create, read, update, and delete tasks in SQLite.

---

## Step 1: Ask Claude to Implement

In Claude Code:

```
Implement the database layer (connection.py and models.py) according to docs/TDD.md sections 2.2.3 and 3.1
```

Claude will:
1. Read your TDD.md
2. Create src/database/connection.py with async connection management
3. Create src/database/models.py with TaskRepository
4. Create the __init__.py files

Select `Yes` when prompted.

---

## Step 2: Review the Changes

In a separate terminal:

```bash
git diff
```

**What to look for:**

| File | Check |
|------|-------|
| `src/database/__init__.py` | Exports connection and repository |
| `src/database/connection.py` | Async context manager, uses aiosqlite |
| `src/database/models.py` | TaskRepository with all CRUD methods |

**TDD specifies these methods (section 2.2.3):**

```python
class TaskRepository:
    async def create(self, title: str, parent_id: int | None = None) -> Task
    async def get_all(self, filter: str = "all", parent_id: int | None = None) -> list[Task]
    async def get_by_id(self, task_id: int) -> Task | None
    async def update_completed(self, task_id: int, completed: bool) -> Task
    async def delete(self, task_id: int) -> bool
    async def create_subtasks(self, parent_id: int, titles: list[str]) -> list[Task]
```

---

## Step 3: Ask Questions

If something is unclear:

```
Why did you use a context manager for the connection?
```

```
How does cascade delete work for subtasks?
```

```
Should the schema be created automatically on first connection?
```

---

## Step 4: Request Adjustments

If something needs changing:

```
Add a method to count tasks by status
```

```
Use the DATABASE_PATH from config.py instead of hardcoding
```

```
Add created_at timestamp to the Task model
```

---

## Step 5: Create Database Tests

Ask Claude to verify:

```
Create tests for the database layer - test all CRUD operations
```

Claude will create `tests/unit/test_database.py` with tests for:
- Creating tasks
- Listing tasks
- Completing tasks
- Deleting tasks
- Subtask operations

### What might happen

**Tests need async support**

pytest needs `pytest-asyncio` to run async tests. Claude will add the appropriate markers:

```python
import pytest

@pytest.mark.asyncio
async def test_create_task():
    ...
```

---

**Tests need a test database**

Claude should use a temporary database for tests, not the real one. Look for:

```python
@pytest.fixture
async def test_db(tmp_path):
    db_path = tmp_path / "test.db"
    ...
```

---

## Step 6: Run Tests

```
Run the database tests
```

### What might happen

**Import errors**

If models.py imports from config.py or other modules, there may be circular imports or missing dependencies. Claude will fix these.

---

**Schema not created**

If tests fail because the table doesn't exist:

```
The tests are failing because the tasks table doesn't exist. Ensure the schema is created in the test fixture.
```

---

## Step 7: Commit

```
Commit this
```

Or with a custom message:

```
Commit with message "feat: add database layer

- Add connection.py with async SQLite management
- Add models.py with TaskRepository
- Add database tests
- Based on TDD sections 2.2.3 and 3.1"
```

Then push:

```
push it
```

---

## Step 8: Update CLAUDE.md

```
Update CLAUDE.md: mark "Database layer" as complete in Implementation Order
```

---

## Done! ✅

**What you learned:**
- aiosqlite for async SQLite operations
- Repository pattern for data access
- Test fixtures with temporary databases
- Async test support with pytest-asyncio

---

## Common Issues

### ModuleNotFoundError: No module named 'aiosqlite'

```
Install aiosqlite - it's missing from the virtual environment
```

### Circular import errors

If connection.py imports from config.py and config.py somehow imports from database:

```
There's a circular import. Can you restructure to avoid it?
```

### Tests polluting real database

```
The tests are using the real database. Use a temporary database in the test fixture.
```

### Async tests not running

Ensure pytest-asyncio is configured in pyproject.toml:

```toml
[tool.pytest.ini_options]
asyncio_mode = "auto"
```

---

## Next

Continue with [tutorial-04-tools.md](./tutorial-04-tools.md)
