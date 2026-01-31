# Tutorial 01: Dependencies

> ⏱️ Time: 20 minutes  
> 📋 Outcome: Project has all dependencies configured and installable

---

## Prerequisites

- Completed [tutorial-claude-code-setup.md](./tutorial-claude-code-setup.md)
- Claude Code running in your project directory

---

## Objective

Configure `pyproject.toml` and `requirements.txt` with all dependencies defined in your TDD.

**Result:** You can run `pip install -r requirements.txt` successfully.

---

## Step 1: Ask Claude to Implement

In Claude Code:

```
Setup project dependencies in pyproject.toml and requirements.txt according to docs/TDD.md section 1.3 (Tech Stack)
```

Claude will:
1. Read your TDD.md
2. Create/update pyproject.toml with project metadata and dependencies
3. Create/update requirements.txt

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
| `pyproject.toml` | Project name, version, Python version, dependencies match TDD |
| `requirements.txt` | All packages from TDD section 1.3 |

---

## Step 3: Ask Questions

If something is unclear or unexpected, ask Claude:

```
Why did you choose version X for package Y?
```

```
The TDD mentions pytest but I don't see it. Can you add it?
```

```
Should aiosqlite be in dependencies or dev-dependencies?
```

---

## Step 4: Request Adjustments

If something needs changing:

```
Move pytest, ruff, and mypy to dev dependencies
```

```
Add python version constraint >= 3.10
```

```
Pin dependency versions for reproducibility
```

---

## Step 5: Verify Installation

In your terminal:

```bash
pip install -r requirements.txt
```

If errors occur, tell Claude:

```
pip install failed with error: [paste error]
```

---

## Step 6: Commit

Once everything works:

```
Commit with message "chore: setup project dependencies

- Add pyproject.toml with project config
- Add requirements.txt with all dependencies
- Based on TDD section 1.3"
```

---

## Step 7: Update CLAUDE.md

```
Update CLAUDE.md: mark "Dependencies" as complete in Implementation Order
```

The checkbox should change from `[ ]` to `[x]`.

---

## Done! ✅

**What you learned:**
- Reference TDD sections for specifications
- Review dependency choices with `git diff`
- Verify by actually installing
- Keep CLAUDE.md updated as progress tracker

---

## Common Issues

### Version conflicts

```
The TDD says Pydantic 2.x but Claude installed 1.x. Fix this.
```

### Missing dev dependencies

```
Add dev dependencies: pytest, pytest-asyncio, ruff, mypy
```

### pyproject.toml vs requirements.txt

Both are valid. `pyproject.toml` is modern Python standard. `requirements.txt` is widely supported. Having both is fine for compatibility.

---

## Next

Continue with [tutorial-02-configuration.md](./tutorial-02-configuration.md)
