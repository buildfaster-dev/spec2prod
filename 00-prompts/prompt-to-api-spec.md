# Prompt: TDD → API Specification

## When to Use
When you have a TDD and need to generate detailed API specifications that serve as a contract for implementation.

## Required Input
- Technical Design Document
- API type (REST, GraphQL, CLI)
- Desired format (OpenAPI, AsyncAPI, custom)

---

## Prompt

```markdown
Act as an API Designer. Generate detailed API specifications based on the following TDD, following the Spec-Driven Development (SDD) approach.

IMPORTANT: This is a new conversation. Do not use any context from previous chats. Only use the information explicitly provided in this prompt.

## TDD
[PASTE TDD HERE]

## API Type
- [ ] REST API (OpenAPI 3.0)
- [x] CLI Commands (Custom spec)
- [ ] GraphQL (Schema)
- [ ] Event-Driven (AsyncAPI)

## Instructions

### For CLI Commands, generate:

#### 1. Command Specification
For each command:
- Name and aliases
- Short and long description
- Arguments (positional)
- Options (flags)
- Usage examples
- Expected output (success and error)

#### 2. Input Validation Rules
- Data types
- Constraints (min, max, pattern)
- Default values
- Error messages

#### 3. Output Format
- Successful output structure
- Error codes and messages
- Format (table, JSON, text)

#### 4. Error Catalog
- List of possible errors
- Exit codes
- User-friendly messages

### Output Format
- Structured markdown
- Executable examples
- Tables for quick reference
```

---

## For REST API (OpenAPI)

```markdown
## Additional instructions for REST

### Generate OpenAPI 3.0 spec with:

1. **Info section**
   - Title, description, version
   - Contact, license

2. **Paths**
   - Each endpoint with unique operationId
   - Request body schemas
   - Response schemas for each status code
   - Request/response examples

3. **Components**
   - Reusable schemas
   - Security schemes
   - Common parameters

4. **Tags**
   - Logical grouping of endpoints
```

---

## Usage Example

**Input:**
```
## TDD
AI-Powered ToDo App

Interface: CLI with Typer
Commands needed: add, list, show, complete, delete, decompose
[... rest of TDD content ...]

## API Type
- [ ] REST API (OpenAPI 3.0)
- [x] CLI Commands (Custom spec)
- [ ] GraphQL (Schema)
- [ ] Event-Driven (AsyncAPI)
```

**How to use:** Copy the Prompt section above, then replace `[PASTE TDD HERE]` with your TDD content and check the appropriate API Type checkbox (REST, CLI, GraphQL, or Event-Driven).

**Expected output:** Complete CLI specification with all 6 commands, including arguments, options, examples, output formats, and error catalog.

---

## Tips

1. **Be exhaustive with errors:** A good spec documents what can go wrong
2. **Real examples:** Don't use "string" as an example, use "Complete API design"
3. **Consistency:** Same patterns across all endpoints/commands
4. **Validation first:** Define constraints before implementing
