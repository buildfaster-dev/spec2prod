# Reference Cheatsheet

> Quick reference for AI Native Development

---

## Claude Code Commands

| Command | Description |
|---------|-------------|
| `claude` | Start interactive session |
| `claude "prompt"` | Execute prompt directly |
| `claude --continue` | Continue last conversation |
| `claude --dangerously-skip-permissions` | Autonomous mode (⚠️ use with care) |
| `/help` | See available commands |
| `/clear` | Clear context |
| `/compact` | Summarize long conversation |
| `/cost` | See tokens used |

---

## Project Slash Commands

| Command | Usage |
|---------|-------|
| `/implement <feature>` | Implement a feature |
| `/test <component>` | Write tests |
| `/fix <bug>` | Investigate and fix bug |

---

## Document Structure

```
00-prompts/              # Transformation prompts
├── prompt-idea-to-prd.md
├── prompt-prd-to-tdd.md
├── prompt-tdd-to-c4.md
├── prompt-to-adr.md
├── prompt-to-api-spec.md
├── prompt-to-claude-md.md
└── prompt-to-test-spec.md

01-guides/               # Guides (Diátaxis)
├── tutorial-claude-code-setup.md
├── tutorial-01-dependencies.md
├── tutorial-02-configuration.md
├── tutorial-03-database.md
├── tutorial-04-tools.md
├── tutorial-05-ui.md
├── tutorial-06-server.md
├── howto-recipes.md
├── reference-cheatsheet.md
└── explanation-pdd.md
```

---

## Your Project Structure

When using spec2prod prompts, your project should look like:

```
your-project/
├── docs/
│   ├── prompts/              # Prompts used (traceability)
│   │   ├── 01-idea-to-prd.md
│   │   └── 02-prd-to-tdd.md
│   ├── ADRs/
│   │   └── ADR-001-xxx.md
│   ├── PRD.md                # Generated outputs
│   ├── TDD.md
│   └── C4-diagrams.md
├── src/
├── tests/
├── CLAUDE.md                 # Root level (required)
└── README.md
```

---

## Transformation Flow

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

| # | Transition | Prompt | Required |
|---|------------|--------|----------|
| 1 | Idea → PRD | `prompt-idea-to-prd.md` | ✅ Yes |
| 2 | PRD → TDD | `prompt-prd-to-tdd.md` | ✅ Yes |
| 3 | TDD → C4 | `prompt-tdd-to-c4.md` | ⚪ Optional |
| 4 | TDD → API Spec | `prompt-to-api-spec.md` | ⚪ Optional |
| 5 | PRD+TDD → Tests | `prompt-to-test-spec.md` | ⚪ Optional |
| 6 | All → CLAUDE.md | `prompt-to-claude-md.md` | ✅ Yes |
| 7 | Decision → ADR | `prompt-to-adr.md` | ⚪ Optional |

**Minimum viable flow:** Idea → PRD → TDD → CLAUDE.md → Code

---

## Diátaxis Framework

| Type | Purpose | Orientation |
|------|---------|-------------|
| **Tutorial** | Learn by doing | Learning-oriented |
| **How-To** | Solve specific problem | Task-oriented |
| **Reference** | Quick lookup | Information-oriented |
| **Explanation** | Understand concepts | Understanding-oriented |

---

## Tech Stack Quick Reference

### Python Packages

```bash
pip install typer[all]      # CLI framework
pip install sqlmodel         # ORM + Pydantic
pip install openai          # OpenAI SDK
pip install python-dotenv   # Env vars
pip install pytest pytest-cov pytest-mock  # Testing
pip install ruff            # Linting
```

### Typer Patterns

```python
# Basic command
@app.command()
def mycommand(name: str):
    """Command description."""
    typer.echo(f"Hello {name}")

# With options
@app.command()
def cmd(
    arg: str = typer.Argument(..., help="Required arg"),
    flag: bool = typer.Option(False, "--flag", "-f"),
):
    pass
```

### SQLModel Patterns

```python
# Model
class Task(SQLModel, table=True):
    id: Optional[int] = Field(default=None, primary_key=True)
    title: str = Field(max_length=200)

# Query
tasks = session.exec(select(Task).where(Task.status == "pending")).all()

# Create
task = Task(title="New task")
session.add(task)
session.commit()
```

### OpenAI SDK Patterns

```python
from openai import OpenAI

client = OpenAI()

response = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[
        {"role": "system", "content": "You are helpful."},
        {"role": "user", "content": prompt}
    ],
    response_format={"type": "json_object"}
)

result = response.choices[0].message.content
```

---

## Testing Patterns

### Fixtures

```python
@pytest.fixture
def db_session():
    engine = create_engine("sqlite:///:memory:")
    SQLModel.metadata.create_all(engine)
    with Session(engine) as session:
        yield session

@pytest.fixture
def task_service(db_session):
    repo = TaskRepository(db_session)
    return TaskService(repo)
```

### Mocking

```python
def test_with_mock(mocker):
    mock = mocker.patch('module.function')
    mock.return_value = expected_value
    # test...
    mock.assert_called_once_with(args)
```

### Async Tests

```python
import pytest

@pytest.mark.asyncio
async def test_async_function():
    result = await async_function()
    assert result == expected
```

---

## Common Prompts

### Explore
```
"What does this project do? Give me a 5-line overview."
"Where is the X logic?"
"Explain the data flow when Y."
```

### Implement
```
"Implement X following the Y pattern."
"Add tests for Z based on test-spec.md."
"Refactor W to use the Strategy pattern."
```

### Debug
```
"Why is this test failing? [test code]"
"I'm seeing this error: [error]. Cause?"
"Add logging to X for debugging."
```

### Document
```
"Update CLAUDE.md with recent changes."
"Generate docstrings for public functions in X."
"Create an ADR for the decision to use Y."
```

---

## Error Codes (CLI)

| Exit | Category |
|------|----------|
| 0 | Success |
| 1 | User Error (invalid input) |
| 2 | External Error (API, DB) |
| 3 | System Error (unexpected) |

---

## Environment Variables

| Variable | Required | Default |
|----------|----------|---------|
| `OPENAI_API_KEY` | Yes (for AI) | - |
| `TODO_DB_PATH` | No | `~/.todo/tasks.db` |
| `TODO_MODEL` | No | `gpt-4o-mini` |

---

*Quick links: [Tutorial](./tutorial-claude-code-setup.md) • [How-To](./howto-recipes.md) • [PDD Explained](./explanation-pdd.md)*
