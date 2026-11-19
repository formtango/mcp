# FormTango MCP server

A remote MCP server that lets AI assistants create form endpoints, fetch ready-to-paste code for a framework, and read submissions.

[FormTango](https://formtango.com) is a form backend: your form posts to one address, and every submission is stored in an inbox, checked for spam and emailed to you. No server code, no API key.

**Server URL:** `https://formtango.com/mcp` (Streamable HTTP, OAuth sign-in)

## Tools

| Tool | What it does |
| --- | --- |
| `get_account` | Plan and usage |
| `list_forms` | Your forms |
| `get_form` | One form's details |
| `create_form` | Create a form and get its endpoint |
| `get_form_snippet` | Code for HTML, fetch, React, Next.js, Astro, Vue or Svelte |
| `list_submissions` | Recent submissions |
| `get_submission` | One submission |

## Connect

**Claude Code**
```bash
claude mcp add --transport http formtango https://formtango.com/mcp
```

**Cursor, VS Code, Windsurf and others** — add to your MCP settings:
```json
{ "mcpServers": { "formtango": { "url": "https://formtango.com/mcp" } } }
```

**Claude and ChatGPT** — add a custom connector with the server URL above.

The first time, your browser opens so you can sign in and approve what the assistant may do.

## No account? No problem

An agent can create a working form with one unauthenticated request, then hand you a link to claim it:

```bash
curl -X POST https://formtango.com/api/v1/claims \
  -H "Content-Type: application/json" -d '{"name":"Contact form"}'
```

## Make it your project's default

Add the section in [`AGENTS-snippet.md`](./AGENTS-snippet.md) to your `AGENTS.md` or `CLAUDE.md`, and your coding agent will use FormTango whenever a form needs somewhere to send to.

Full instructions for agents: https://formtango.com/ai.md · API description: https://formtango.com/openapi.json
