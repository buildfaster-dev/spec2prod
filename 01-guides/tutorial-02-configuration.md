# Tutorial 02: Configuration

> ⏱️ Time: 15 minutes  
> 📋 Outcome: Project has configuration management with environment variables

---

## Prerequisites

- Completed [tutorial-01-dependencies.md](./tutorial-01-dependencies.md)
- Claude Code running in your project directory

---

## Objective

Create `config.py` and `.env.example` for configuration management.

**Result:** Application settings loaded from environment variables with sensible defaults.

---

## Step 1: Ask Claude to Implement

In Claude Code:

```
Implement config.py and .env.example according to docs/TDD.md
```

Claude will:
1. Read your TDD.md
2. Create src/config.py with settings class
3. Create .env.example with documented variables

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
| `src/config.py` | Settings class, environment variable loading, defaults |
| `.env.example` | All variables documented with example values |

---

## Step 3: Ask Questions

If something is unclear:

```
Why did you use pydantic-settings instead of python-dotenv?
```

```
Should DATABASE_URL have a default value?
```

```
How do I override these settings in tests?
```

---

## Step 4: Request Adjustments

If something needs changing:

```
Add a DEBUG setting that defaults to False
```

```
Move the database path to a DATA_DIR setting
```

```
Add validation to ensure PORT is between 1-65535
```

---

## Step 5: Verify Configuration Loads

Ask Claude to verify:

```
Create a simple test to verify config loads correctly
```

Or test manually in Python:

```bash
source .venv/bin/activate
python -c "from src.config import settings; print(settings)"
```

---

## Step 6: Commit

```
Commit this
```

Or with a custom message:

```
Commit with message "feat: add configuration management

- Add src/config.py with Settings class
- Add .env.example with documented variables
- Based on TDD configuration section"
```

---

## Step 7: Update CLAUDE.md

```
Update CLAUDE.md: mark "Configuration" as complete in Implementation Order
```

---

## Done! ✅

**What you learned:**
- Configuration should be separate from code
- Environment variables for secrets and environment-specific settings
- .env.example documents required variables without exposing secrets
- Pydantic Settings provides validation and type conversion

---

## Common Issues

### Import error: config not found

Ensure `src/__init__.py` exists:

```
Create src/__init__.py if it doesn't exist
```

### Environment variables not loading

```
The .env file isn't being loaded. Check if python-dotenv or pydantic-settings is configured correctly.
```

### Settings validation fails

```
Config validation is failing with error: [paste error]
```

---

## Next

Continue with [tutorial-03-database.md](./tutorial-03-database.md)
