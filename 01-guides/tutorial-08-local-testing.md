# Tutorial 08: Local Testing with ChatGPT

> ⏱️ Time: 30 minutes
> 📋 Outcome: Your MCP server connected to ChatGPT running from localhost

---

## Prerequisites

- Completed [tutorial-07-tests.md](./tutorial-07-tests.md)
- ChatGPT Plus subscription (for custom GPTs)
- Cloudflare account (free)

---

## Objective

Expose your local server to the internet and connect it to ChatGPT.

**Result:** Talk to ChatGPT and manage tasks through your MCP server.

---

## Step 1: Verify Nix is Available

```bash
nix --version
```

No installation needed - we'll run cloudflared directly with `nix run`.

---

## Step 2: Start Your Server

In one terminal:

```bash
cd chatgpt-todo-app
source .venv/bin/activate
uvicorn src.server:app --host 0.0.0.0 --port 8000 --proxy-headers
```

Note:
- `--host 0.0.0.0` allows external connections
- `--proxy-headers` handles headers from Cloudflare tunnel

---

## Step 3: Start Cloudflare Tunnel

In another terminal:

```bash
nix run nixpkgs#cloudflared -- tunnel --url http://localhost:8000
```

You'll see:

```
Your quick Tunnel has been created! Visit it at:
https://xxxx-xxxx-xxxx.trycloudflare.com
```

Copy the `https://...trycloudflare.com` URL.

> No account needed for quick tunnels. The URL changes each restart.

---

## Step 4: Test the Public URL

```bash
curl -X POST "https://YOUR-CLOUDFLARE-URL/mcp" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "initialize",
    "params": {
      "protocolVersion": "2025-03-26",
      "capabilities": {},
      "clientInfo": {"name": "test", "version": "1.0"}
    }
  }'
```

If you get a response with `serverInfo`, it works!

> The session ID is in the response **headers**, not the body. Use `curl -s -D -` to see headers. For ChatGPT, you don't need to worry about session ID - ChatGPT handles it automatically.

---

## Step 5: Create a Custom GPT

1. Go to [chat.openai.com](https://chat.openai.com)
2. Click your profile → **My GPTs** → **Create a GPT**
3. In the **Configure** tab:

**Name:** Todo App

**Description:** Manage tasks with AI-powered decomposition

**Instructions:**
```
You are a task management assistant. Use the available tools to help users:
- Add new tasks
- List their tasks
- Mark tasks as complete
- Delete tasks
- Decompose complex tasks into subtasks

Always show the task list after making changes.
```

---

## Step 6: Add Actions

1. Click **Create new action**
2. Select **Import from URL**
3. Enter: `https://YOUR-CLOUDFLARE-URL/mcp/openapi.json`

If that doesn't work, ask Claude Code:

```
Generate an OpenAPI spec for the MCP server actions
```

**Alternative: Manual configuration**

If the server doesn't expose OpenAPI, configure actions manually:

| Action | Method | Endpoint |
|--------|--------|----------|
| Initialize | POST | /mcp |
| Add Task | POST | /mcp |
| List Tasks | POST | /mcp |
| Complete Task | POST | /mcp |
| Delete Task | POST | /mcp |

The body format is JSON-RPC as tested with curl.

---

## Step 7: Test in ChatGPT

Try these prompts:

```
Add a task: Buy groceries
```

```
Show me my tasks
```

```
Complete task 1
```

```
Break down "Plan birthday party" into subtasks
```

---

## Done! ✅

**What you learned:**
- Cloudflare Tunnel exposes localhost to the internet (no account needed)
- ChatGPT custom GPTs can connect to external APIs
- MCP protocol works with ChatGPT Actions
- Local development → test with real AI

---

## Common Issues

### "context canceled" errors in Cloudflare tunnel

```
ERR error="context canceled" connIndex=0 event=1 ingressRule=0 originService=http://localhost:8000
ERR failed to serve incoming request error="Failed to proxy HTTP: context canceled"
```

This is normal. It happens when ChatGPT closes the connection before the server finishes responding. It doesn't affect functionality.

### Cloudflare URL changes every restart

Quick tunnels give random URLs. For persistent URLs:
- Create a Cloudflare account
- Set up a named tunnel with custom domain

### "Invalid Host header" or 421 Misdirected Request

The server rejects requests from Cloudflare tunnel because the Host header doesn't match localhost.

In Claude Code:

```
The server returns "Invalid Host header" and 421 Misdirected Request when accessed via Cloudflare tunnel. Fix this by adding TrustedHostMiddleware or removing host validation to allow requests from any host during development.
```

### ChatGPT can't reach the server

1. Verify the nix run cloudflared command is still running
2. Test the URL with curl first
3. Check server logs for errors

### CORS errors

Add CORS headers in server.py:

```
Add CORS middleware to allow requests from ChatGPT
```

### Actions not working

The MCP protocol may need adaptation for ChatGPT Actions. Ask Claude:

```
Create a REST adapter that exposes MCP tools as simple REST endpoints for ChatGPT Actions
```

### Session management

ChatGPT may not maintain session state between requests. You might need:

```
Make the server stateless or add automatic session initialization
```

---

## Development Workflow

```
1. Make changes to code
2. Server auto-reloads (--reload flag)
3. Test in ChatGPT immediately
4. Iterate quickly
```

Keep both terminals running:
- Terminal 1: uvicorn (server)
- Terminal 2: nix run cloudflared (tunnel)

---

## Next

Continue with [tutorial-09-production.md](./tutorial-09-production.md)
