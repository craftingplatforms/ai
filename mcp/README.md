# MCP Servers

Model Context Protocol servers that extend AI with domain-specific tools. MCP is vendor-neutral — the same server works with Claude Code, Cursor, GitHub Copilot, and any other MCP-compatible client.

Where skills teach an AI *how* to approach a task, MCP servers give it *live access* to data: query Terraform state, read metrics, browse a service catalog, explore cloud costs.

## When to build an MCP server vs. a skill

| Use a **skill** when | Use an **MCP server** when |
|---------------------|--------------------------|
| The AI needs reasoning guidance | The AI needs live data from an external system |
| The task is self-contained | The task requires querying an API or database |
| Context can be gathered by reading files | Context requires real-time or dynamic information |

## Artifact format

Each MCP server lives in its own subdirectory:

```
mcp/
└── server-name/
    ├── README.md        # what it does, how to install and configure
    ├── index.js         # server implementation (or main.py, etc.)
    └── package.json     # (or requirements.txt, go.mod, etc.)
```

The server's `README.md` must include:
- What tools the server exposes
- Installation steps
- Configuration (environment variables, settings.json snippet)
- An example of a prompt that benefits from this server

## Claude Code configuration

```json
{
  "mcpServers": {
    "server-name": {
      "command": "node",
      "args": [".claude/mcp/server-name/index.js"],
      "env": { "API_KEY": "..." }
    }
  }
}
```

## Contributing an MCP server

Read [CONTRIBUTING.md](../CONTRIBUTING.md) for the full process and PR checklist.
