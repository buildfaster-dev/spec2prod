# Tutorial: Your First Task with Claude Code

> ⏱️ Time: 20 minutes  
> 📋 Outcome: Complete one task using Claude Code in your project

---

## Prerequisites

- Claude Pro or Max subscription, OR Anthropic API key
- A project with `CLAUDE.md` at root (see `00-prompts/prompt-to-claude-md.md`)

---

## Step 1: Install

**macOS / Linux:**
```bash
curl -fsSL https://claude.ai/install.sh | bash
source ~/.zshrc  # or ~/.bashrc
```

**macOS with Homebrew:**
```bash
brew install --cask claude-code
```

**Windows:**
```powershell
irm https://claude.ai/install.ps1 | iex
```

Verify:
```bash
claude --version
```

> 📖 Problems? See [Troubleshooting](#troubleshooting) or [Official Docs](https://docs.anthropic.com/en/docs/claude-code/setup)

---

## Step 2: Authenticate

```bash
claude
```

Inside Claude Code, type:
```
/login
```

Follow browser prompts to sign in. When done, you'll see a welcome screen.

---

## Step 3: Open Your Project

Exit and navigate to your project:
```
/exit
```

```bash
cd path/to/your-project
claude
```

---

## Step 4: Verify Claude Understands Your Project

```
What does this project do?
```

Claude should answer based on your `CLAUDE.md`. If the answer is wrong or vague, your `CLAUDE.md` needs more detail.

---

## Step 5: Delegate a Task

Ask Claude to do something concrete:

```
Create the directory structure defined in CLAUDE.md
```

Claude will:
1. Read your CLAUDE.md
2. Ask permission before executing commands
3. Create the files and folders

Select `Yes` when prompted.

---

## Step 6: Review Changes

In a separate terminal:

```bash
git status
```

Verify the files match what you expected.

---

## Step 7: Commit

Back in Claude Code:

```
Commit this with message "chore: create initial project structure"
```

Claude runs `git add` + `git commit`. Select `Yes` when prompted.

Optional - push:
```
push it
```

---

## Done! 🎉

You completed your first task with Claude Code.

**What you learned:**
- Describe what you want, Claude executes
- Always review with `git status` or `git diff`
- Commit after each completed task

---

## Next Steps

- Try: "Implement the database layer" 
- Review actual code with `git diff`
- See [How-To Recipes](./howto-recipes.md) for common tasks
- See [PDD Explained](./explanation-pdd.md) to understand the workflow

---

## Troubleshooting

### "command not found: claude"

Add to PATH manually:
```bash
export PATH="$HOME/.local/bin:$PATH"
```

For Nix/home-manager users: add this to your shell configuration permanently, or run it each session.

### Authentication fails

```bash
claude /logout
claude /login
```

### Claude doesn't understand my project

Your `CLAUDE.md` is incomplete. Regenerate it using `00-prompts/prompt-to-claude-md.md` with more detail.

### Other issues

Run diagnostics:
```bash
claude doctor
```

See [Official Troubleshooting Guide](https://docs.anthropic.com/en/docs/claude-code/troubleshooting)
