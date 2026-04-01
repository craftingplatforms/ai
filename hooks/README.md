# Hooks

Shell scripts triggered by AI tool lifecycle events — before or after a tool call, when the session stops, or on notifications. Hooks enable automated validation, notifications, and guardrails without manual intervention.

Currently Claude Code-specific, but the pattern is emerging across AI platforms.

## Events

| Event | When it fires | Common uses |
|-------|--------------|-------------|
| `PreToolUse` | Before a tool call | Block risky commands, validate inputs |
| `PostToolUse` | After a tool call | Validate outputs, run tests, notify |
| `Stop` | Session ends | Summaries, cleanup, notifications |
| `Notification` | Claude Code notifications | Alerts, logging |

## Hook contract

- **Exit 0** → success, AI continues normally
- **Exit non-zero** → failure, AI sees stdout/stderr and can react
- Hooks receive context via environment variables and stdin

## Artifact format

Executable shell script in `hooks/`. Name it clearly after its trigger and purpose:

```
hooks/
├── post-write-validate-terraform.sh
├── pre-bash-check-secrets.sh
└── stop-notify-slack.sh
```

Each hook should include a header comment explaining:
- What event triggers it
- What it checks or does
- What a non-zero exit means

## Claude Code configuration

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write",
        "hooks": [{ "type": "command", "command": ".claude/hooks/post-write-validate-terraform.sh" }]
      }
    ]
  }
}
```

## Contributing a hook

Read [CONTRIBUTING.md](../CONTRIBUTING.md) for the full process and PR checklist.
