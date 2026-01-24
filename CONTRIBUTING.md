# Contributing to spec2prod

Thanks for your interest in contributing! 🎉

## How to Contribute

### 1. Reporting Issues

- **Bugs:** Describe the problem, steps to reproduce, and expected behavior
- **Features:** Explain the use case and how it fits in the [Roadmap](./ROADMAP.md)
- **Docs:** Point out errors, improvements, or confusing sections

### 2. Pull Requests

#### For Documentation

1. Fork the repository
2. Create a branch: `git checkout -b docs/my-improvement`
3. Make your changes
4. Ensure links work
5. Create a PR with clear description

#### For Prompts

1. Test the prompt multiple times before proposing
2. Include input and output examples
3. Document known edge cases

#### For New Features

1. Open an issue first to discuss
2. Reference the issue in your PR
3. Include documentation

### 3. Standards

#### Document Structure

```markdown
# Title

> Brief description (1 line)

---

## Section 1

Content...

---

## Changelog

| Date | Change |
|------|--------|
```

#### File Naming

- Lowercase with hyphens: `my-document.md`
- Prompts: `prompt-[input]-to-[output].md`
- ADRs: `ADR-XXX-keyword.md`

#### Commits

```
type(scope): brief description

- detail 1
- detail 2
```

Types: `docs`, `feat`, `fix`, `refactor`, `chore`

### 4. Areas of Contribution

| Area | Description | Level |
|------|-------------|-------|
| Typos/clarity | Fix errors, improve wording | 🟢 Easy |
| Examples | Add examples to existing docs | 🟢 Easy |
| Translations | Translate to other languages | 🟡 Medium |
| New prompts | Create transformation prompts | 🟡 Medium |
| Stage 2 | Features for Agentic Development | 🔴 Advanced |

### 5. Code of Conduct

- Be respectful
- Assume good intentions
- Constructive feedback
- Help other contributors

---

## Local Setup

```bash
# Clone
git clone https://github.com/[your-username]/spec2prod.git
cd spec2prod

# View structure
tree -L 2

# Test a prompt
# Open Claude and use the content from 00-prompts/prompt-idea-to-prd.md
```

## Questions

Open an issue with the `question` label or start a discussion.

---

*Built with ❤️ for the spec2prod community*
