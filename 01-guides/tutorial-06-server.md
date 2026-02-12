# Tutorial 06: Server

> ⏱️ Time: 30 minutes
> 📋 Outcome: MCP server that registers all tools and handles HTTP transport

---

## Prerequisites

- Completed [tutorial-05-ui.md](./tutorial-05-ui.md)
- Claude Code running in your project directory

---

## Objective

Create `server.py` that:
- Initializes the MCP server
- Registers all tool handlers
- Handles HTTP transport with uvicorn

**Result:** A running MCP server that ChatGPT can connect to.

---

## Step 1: Implement Server

In Claude Code:

```
Implement src/server.py according to docs/TDD.md section 2.2.1 (MCP Server)
```

Claude will:
1. Read your TDD.md
2. Create the MCP server entry point
3. Register all tools from task_tools.py
4. Configure HTTP transport

Select `Yes` when prompted.

---

## Step 2: Review the Changes

In a separate terminal:

```bash
git diff src/server.py
```

**What to look for:**

| Check | Description |
|-------|-------------|
| Server initialization | `Server("todo-app")` or similar |
| Tool registration | All 5 tools registered |
| HTTP transport | uvicorn or StreamableHTTPServerTransport |
| Async handlers | All functions use async/await |

---

## Step 3: Start the Server

In a terminal (not Claude Code):

```bash
cd chatgpt-todo-app
source .venv/bin/activate
uvicorn src.server:app --reload --port 8000
```

You should see:

```
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
INFO:     Started server process [...]
INFO:     Waiting for application startup.
INFO:     mcp.server.streamable_http_manager: StreamableHTTP session manager started
INFO:     Application startup complete.
```

---

## Step 4: Test the Server

The MCP server uses JSON-RPC over HTTP POST at `/mcp`. Here's how to test:

### Initialize a session

```bash
curl -s -D - -X POST "http://localhost:8000/mcp" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "initialize",
    "params": {
      "protocolVersion": "2025-03-26",
      "capabilities": {},
      "clientInfo": {"name": "curl-test", "version": "1.0"}
    }
  }'
```

Copy the `mcp-session-id` from the response headers.

### List available tools

```bash
curl -s -X POST "http://localhost:8000/mcp" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -H "mcp-session-id: YOUR_SESSION_ID" \
  -d '{"jsonrpc":"2.0","id":2,"method":"tools/list","params":{}}'
```

You should see all 5 tools: `add_task`, `list_tasks`, `complete_task`, `delete_task`, `decompose_task`.

### Call a tool

```bash
curl -s -X POST "http://localhost:8000/mcp" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -H "mcp-session-id: YOUR_SESSION_ID" \
  -d '{"jsonrpc":"2.0","id":3,"method":"tools/call","params":{"name":"add_task","arguments":{"title":"Buy groceries"}}}'
```

Expected response includes:

```json
{"task": {"id": 1, "title": "Buy groceries", "completed": 0, ...}, "ui": "<inline-card>Task created: Buy groceries</inline-card>"}
```

### Create a test script

Ask Claude Code:

```
Create a test-curl.sh script that tests all MCP endpoints: initialize, list tools, add task, list tasks, complete task, decompose task, delete task
```

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
Update CLAUDE.md: mark "Server" as complete in Implementation Order
```

---

## Done! ✅

**What you learned:**
- MCP server as the entry point
- Tool registration pattern
- HTTP transport with uvicorn
- JSON-RPC protocol for MCP communication
- Session-based API (requires mcp-session-id header)

---

## Common Issues

### "Not Found" on GET requests

MCP uses POST with JSON-RPC, not GET:

```bash
# Wrong
curl http://localhost:8000/

# Correct
curl -X POST http://localhost:8000/mcp -H "Content-Type: application/json" -d '...'
```

### Missing session ID

Every request after initialize needs the `mcp-session-id` header from the initialize response.

### ModuleNotFoundError

```
Fix the import error: [paste error]
```

### Port already in use

```bash
# Find what's using the port
lsof -i :8000

# Use a different port
uvicorn src.server:app --reload --port 8001
```

### MCP SDK version mismatch

The TDD pseudocode may not match the actual MCP SDK:

```
Check the mcp package documentation for the correct way to register tools
```

---

## Next

Continue with [tutorial-07-tests.md](./tutorial-07-tests.md)
