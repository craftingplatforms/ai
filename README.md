# Crafting Platforms — AI Artifacts

Build and train AI agents to architect internal developer platforms. This repository contains reusable skills, commands, agents, and configurations for major AI platforms (Claude Code, GitHub Copilot, Cursor). Closely related to the [**Crafting Platforms**](https://craftingplatforms.com) book — but open to any platform engineering or AI best practice.

## What Is This?

Instead of manually architecting your platform, **teach an AI agent to do it**. This repository provides pre-built, production-ready artifacts that guide AI through platform engineering tasks: designing segmentation strategies, scaffolding infrastructure, auditing security, automating CI/CD, and more.

Many artifacts here relate to chapters in *Crafting Platforms*, bridging human guidance (the book) and machine execution (the code). Others are grounded in platform engineering or AI best practices — the repository grows with the community.

## The Book: Crafting Platforms

**By Ezequiel Foncubierta**

A practical guide to building opinionated, made-to-measure internal developer platforms that fit your organization's unique DNA.

> Platform craftsmanship, not platform manufacturing.

### Why This Book + This Repo?

The book teaches **humans** the principles and patterns for building platforms. This repository teaches **AI agents** how to implement them. Together, they form a complete system: strategic guidance for people, executable instructions for machines.

- **Read the book** to understand *why* we build platforms and *how* to design them for your org
- **Use the AI artifacts** to implement the book's concepts with less manual work

### Get the Book

- **Website**: [craftingplatforms.com](https://www.craftingplatforms.com) — project home, about the author, and links
- **Early Access** (digital): [leanpub.com/crafting-platforms](https://leanpub.com/crafting-platforms) — get chapters as they're published
- **Newsletter**: [newsletter.craftingplatforms.com](https://newsletter.craftingplatforms.com) — practical articles, platform engineering insights, and early announcements

## Book Chapters

| Chapter | Topic |
|---------|-------|
| 0 | Preface |
| 1 | Introduction |
| 2 | Internal Developer Platform |
| 3 | Segmentation |
| 4 | Infrastructure |
| 5 | CI/CD |
| 6 | Observability |
| 7 | Security and Compliance |
| 8 | Developer Experience |

Artifacts tied to book chapters will be added as the book is completed. Community contributions grounded in platform engineering best practices are also welcome. See the [Artifact Inventory](#artifact-inventory) to track progress.

---

## Project Structure

```
ai/
├── skills/                  # Reusable AI skills (one per task)
├── commands/                # Chat/slash commands (workflows)
├── agents/                  # Specialized agent definitions
├── hooks/                   # Event-driven automation scripts
├── mcp/                     # Model Context Protocol servers
├── vendors/                 # Deployment adapters per AI platform
│   ├── claude-code/
│   ├── cursor/
│   └── github-copilot/
├── README.md                # This file (landing page + docs)
└── CLAUDE.md                # Development guidelines
```

**Design principle:** Artifacts are written **vendor-agnostically**. The `vendors/` directory contains thin adapters explaining how to deploy each artifact to your AI platform of choice.

---

## Getting Started

### For Users: Install Artifacts

#### Claude Code

**Option 1: Using [skills.sh](https://skills.sh) (recommended)**

```bash
npx skills add https://github.com/craftingplatforms/ai
```

**Option 2: Manual copy**

```bash
# Global (all projects)
cp skills/*.md ~/.claude/skills/

# Per-project
mkdir -p your-project/.claude/skills/
cp skills/*.md your-project/.claude/skills/
```

Support for additional AI platforms (GitHub Copilot, Cursor, etc.) is planned for future releases.

### For Developers: Build New Artifacts

#### Creating a Skill

A skill is a self-contained, vendor-agnostic set of instructions for an AI to accomplish a platform engineering task.

**Location:** `skills/skill-name.md`

**Format:**

```markdown
---
name: skill-name
description: One sentence — when to invoke this skill (used for matching).
---

# Skill Title

## Your Goal

[What the AI should accomplish]

## What to Gather First

[Questions to ask the user or context to infer]

## Process

[Step-by-step approach]

## Output Format

[Expected deliverables]

## Related Chapter

This skill corresponds to **Chapter N: Chapter Name** of *Crafting Platforms* by Ezequiel Foncubierta.
See [craftingplatforms.com](https://www.craftingplatforms.com) to read more.
```

**Guidelines:**

- Write for an AI, not a human. Be explicit about every step.
- Include enough context so the skill works standalone.
- If the skill relates to a book chapter, link to it for deeper understanding.
- No Terraform, Kubernetes, or application code — that goes in the book's examples or separate repos. The skill teaches the *approach*, not the implementation details.

#### Creating a Command

A command is a named workflow invoked via slash (`/command-name`).

**Location:** `commands/command-name.md`

**Format:** Same as skills, but typically shorter and more focused on a repeatable action within a project.

#### Creating an Agent

An agent is a specialized AI with a focused system prompt, narrow tool set, and specific responsibilities.

**Location:** `agents/agent-name.md`

**Format:**

```markdown
---
name: agent-name
description: When to spawn this agent (used for routing).
tools: [Read, Grep, Bash]  # tools the agent can use
---

[Agent system prompt — full context and instructions]
```

#### Creating a Hook

Hooks are shell scripts triggered by AI tool lifecycle events (pre-tool, post-tool, on-stop, etc.). Currently Claude Code-specific, but the pattern is emerging across platforms.

**Location:** `hooks/hook-name.sh`

**Format:** Executable shell script. Receives context via environment variables and stdin.

#### Creating an MCP Server

Model Context Protocol servers extend Claude with domain-specific tools (query Terraform state, read metrics, etc.). MCP is vendor-neutral — works with any MCP-compatible client.

**Location:** `mcp/server-name/` with `index.js`, `requirements.txt`, etc.

**Format:** Depends on language. Includes a `README.md` with setup instructions.

### Workflow: From Idea to Artifact

1. **Identify the need** → Book chapter being published, a best practice worth encoding, or a community request
2. **Design the artifact** → Skill? Command? Agent? Depends on the use case
3. **Write vendor-agnostically** → Place in `skills/`, `commands/`, etc.
4. **Test** → Verify the artifact works with real platform engineers
5. **Cross-reference** → If the artifact relates to a book chapter, link to it

---

## Artifact Inventory

Currently **empty**. Skills, commands, agents, and MCP servers will be developed and published as corresponding book chapters are completed.

**Check the [`skills/`](skills/), [`commands/`](commands/), [`agents/`](agents/), and [`mcp/`](mcp/) directories for the latest artifacts, and subscribe to the [newsletter](https://newsletter.craftingplatforms.com) for announcements when new artifacts are released.**

---

## Philosophy

**Opinionated.** The artifacts here reflect the book's philosophy: platforms should be tailored to your org, built with clear principles, and designed for autonomy.

**Practical.** Every artifact is grounded in real-world platform engineering. No toy examples.

**Transparent.** You should understand why an artifact makes specific recommendations. Read the book chapter to see the reasoning.

**Extensible.** Fork or modify artifacts for your specific needs. These are starting points, not constraints.

---

## Connect

- **Website:** [craftingplatforms.com](https://www.craftingplatforms.com) — project home
- **Early Access:** [leanpub.com/crafting-platforms](https://leanpub.com/crafting-platforms) — chapters as published
- **Newsletter:** [newsletter.craftingplatforms.com](https://newsletter.craftingplatforms.com) — practical articles on platform engineering
- **GitHub:** [github.com/craftingplatforms](https://github.com/craftingplatforms)
- **Author:** Ezequiel Foncubierta — [foncubierta.com](https://foncubierta.com) — [@foncubierta.com on Bluesky](https://bsky.app/profile/foncubierta.com)

---

## License

Apache 2.0 — see [LICENSE](LICENSE) for details.

Free to use, fork, and build upon. The book and these artifacts are designed to share knowledge, not to lock it away.

---

## Contributing

Found an issue or have an idea? Open a GitHub issue or pull request. Contributions that improve clarity, add platform support, or extend the artifact library are welcome.

Before contributing new artifacts, check the [CLAUDE.md](CLAUDE.md) for development guidelines.

---

**Build the platform your org deserves. Start with the book, execute with the code.**
