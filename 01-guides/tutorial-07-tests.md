# Tutorial 07: Tests & Quality

> ⏱️ Time: 20 minutes
> 📋 Outcome: All tests passing with coverage report, linting, and type checking

---

## Prerequisites

- Completed [tutorial-06-server.md](./tutorial-06-server.md)
- Claude Code running in your project directory

---

## Objective

Run full test suite and quality checks:
- pytest with coverage report
- ruff for linting
- mypy for type checking

**Result:** Clean codebase ready for production.

---

## Step 1: Run All Tests with Coverage

In Claude Code:

```
Run all tests with coverage report
```

Or in terminal:

```bash
source .venv/bin/activate
pytest --cov=src --cov-report=term-missing
```

You should see:

```
================== test session starts ==================
...
================== X passed in Y.XXs ==================

---------- coverage: ... ----------
Name                          Stmts   Miss  Cover   Missing
-----------------------------------------------------------
src/config.py                    XX      X    XX%
src/database/connection.py       XX      X    XX%
src/database/models.py           XX      X    XX%
...
-----------------------------------------------------------
TOTAL                           XXX     XX    XX%
```

### What might happen

**Missing test dependencies**

```
Add pytest-cov to dev dependencies if missing
```

**Low coverage on some modules**

That's okay for now. The goal is to verify everything runs, not 100% coverage.

---

## Step 2: Run Linting

In Claude Code:

```
Run ruff to check for linting issues
```

Or in terminal:

```bash
ruff check src/
```

### What might happen

**Linting errors found**

```
Fix the ruff linting errors
```

Claude will auto-fix most issues. Common ones:
- Unused imports
- Line too long
- Missing whitespace

---

## Step 3: Run Type Checking

In Claude Code:

```
Run mypy to check types
```

Or in terminal:

```bash
mypy src/
```

### What might happen

**Type errors**

```
Fix the mypy type errors
```

Common issues:
- Missing return types
- Incompatible types
- Missing type annotations

---

## Step 4: Fix Any Issues

If there are errors from the previous steps:

```
Fix all linting and type errors
```

Claude will iterate until everything passes.

---

## Step 5: Commit

```
commit this
```

Then push:

```
push it
```

---

## Step 6: Update CLAUDE.md

```
Update CLAUDE.md: mark "Tests" as complete in Implementation Order
```

---

## Done! ✅

**What you learned:**
- pytest --cov for coverage reports
- ruff for fast Python linting
- mypy for static type checking
- Quality tools catch bugs before production

---

## Common Issues

### pytest-cov not installed

```
pip install pytest-cov
```

Or ask Claude:

```
Add pytest-cov to dev dependencies and install it
```

### ruff not found

```
pip install ruff
```

### mypy errors on third-party packages

Add to pyproject.toml:

```toml
[tool.mypy]
ignore_missing_imports = true
```

### Too many errors to fix

Focus on critical ones first:

```
Fix only the errors in src/server.py and src/tools/
```

---

## Summary

| Check | Command | Purpose |
|-------|---------|---------|
| Tests | `pytest --cov=src` | Verify functionality |
| Lint | `ruff check src/` | Code style |
| Types | `mypy src/` | Type safety |

---

## Next

Continue with [tutorial-08-production.md](./tutorial-08-production.md)
