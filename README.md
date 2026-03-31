# Crafting Platforms — AI Artifacts

Build and train AI agents to architect internal developer platforms. This repository contains reusable skills, commands, agents, and configurations for major AI platforms (Claude Code, GitHub Copilot, Cursor), all grounded in the concepts from the **Crafting Platforms** book.

## What Is This?

Instead of manually architecting your platform, **teach an AI agent to do it**. This repository provides pre-built, production-ready artifacts that guide AI through platform engineering tasks: designing segmentation strategies, scaffolding infrastructure, auditing security, automating CI/CD, and more.

Every artifact here maps to a chapter in *Crafting Platforms*, ensuring alignment between human guidance (the book) and machine execution (the code).

## The Book: Crafting Platforms

**By Ezequiel Foncubierta**

A practical guide to building opinionated, made-to-measure internal developer platforms that fit your organization's unique DNA.

> Platform craftsmanship, not platform manufacturing.

### Why This Book + This Repo?

The book teaches **humans** the principles and patterns for building platforms. This repository teaches **AI agents** how to implement them. Together, they form a complete system: strategic guidance for people, executable instructions for machines.

- **Read the book** to understand *why* we build platforms and *how* to design them for your org
- **Use the AI artifacts** to implement the book's concepts with less manual work

### Get the Book

- **Early Access** (digital): [craftingplatforms.com](https://www.craftingplatforms.com) — $29 for chapters as they're published
- **Leanpub** (when complete): Full book in PDF and ePub
- **Newsletter**: [newsletter.craftingplatforms.com](https://newsletter.craftingplatforms.com) — practical articles, platform engineering insights, and early announcements

## Table of Contents (Book Chapters)

| Chapter | Topic | AI Artifacts |
|---------|-------|-------------|
| 1 | Introduction | — |
| 2 | Internal Developer Platform | — |
| 3 | Segmentation | `segmentation-designer` (skill) |
| 4 | Infrastructure | `infrastructure-scaffolder` (skill) |
| 5 | CI/CD | `pipeline-generator` (skill) |
| 6 | Observability | `observability-setup` (skill) |
| 7 | Security and Compliance | `security-auditor` (skill) |
| 8 | Developer Experience | `devex-improver` (skill) |

*Artifacts will be added as chapters are published.*

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

### For Users: Deploy Artifacts to Your AI Platform

#### Claude Code

Copy skills globally or per-project:

```bash
# Global (all projects)
cp skills/*.md ~/.claude/skills/

# Per-project
mkdir -p your-project/.claude/skills/
cp skills/*.md your-project/.claude/skills/
```

Then invoke in Claude Code:
```
Help me design a platform segmentation strategy using the design-segmentation skill.
```

See [`vendors/claude-code/README.md`](vendors/claude-code/README.md) for full setup.

#### GitHub Copilot

Copy the consolidated instructions to your repo:

```bash
mkdir -p your-project/.github/
cp vendors/github-copilot/platform-engineer.md your-project/.github/copilot-instructions.md
```

See [`vendors/github-copilot/README.md`](vendors/github-copilot/README.md) for details.

#### Cursor

Copy rules to your workspace:

```bash
mkdir -p your-project/.cursor/rules/
cp vendors/cursor/platform-engineer.mdc your-project/.cursor/rules/
```

See [`vendors/cursor/README.md`](vendors/cursor/README.md) for details.

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
- Include enough context so the skill works standalone, but reference the book chapter for deeper understanding.
- Always end with a link to the corresponding book chapter.
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

### Workflow: From Book Chapter to AI Artifact

1. **Chapter published** → Add entry to the table above
2. **Design the artifact** → Skill? Command? Agent? Depends on the use case
3. **Write vendor-agnostically** → Place in `skills/`, `commands/`, etc.
4. **Add vendor adapters** → Update `vendors/` with platform-specific docs if needed
5. **Test** → Verify the artifact works with real platform engineers
6. **Cross-reference** → Ensure the artifact is discoverable from the book chapter

---

## Artifact Inventory

**Skills** (machine-executable approaches to platform tasks):

| Name | Chapter | Status |
|------|---------|--------|
| `design-segmentation` | Ch. 3 | Planned (Q2 2026) |
| `scaffold-infra` | Ch. 4 | Planned (Q3 2026) |
| `generate-pipeline` | Ch. 5 | Planned (Q3 2026) |
| `setup-observability` | Ch. 6 | Planned (Q4 2026) |
| `audit-security` | Ch. 7 | Planned (Q4 2026) |
| `improve-devex` | Ch. 8 | Planned (Q1 2027) |

**Commands** (repeatable workflows):

| Name | Purpose | Status |
|------|---------|--------|
| `/platform-review` | Review a PR for platform standards | Planned |
| `/cost-report` | Generate cost attribution by team | Planned |
| `/infra-drift` | Detect Terraform drift | Planned |

**Agents** (specialized sub-agents):

| Name | Focus | Status |
|------|-------|--------|
| `infra-reviewer` | Code review for infrastructure | Planned |
| `slo-designer` | SLO/SLI design | Planned |

**MCP Servers:**

| Server | Purpose | Status |
|--------|---------|--------|
| `terraform-state` | Query Terraform state | Planned |
| `platform-catalog` | Read from service catalog | Planned |
| `observability` | Query metrics and logs | Planned |

---

## Philosophy

**Opinionated.** The artifacts here reflect the book's philosophy: platforms should be tailored to your org, built with clear principles, and designed for autonomy.

**Practical.** Every artifact is grounded in real-world platform engineering. No toy examples.

**Transparent.** You should understand why an artifact makes specific recommendations. Read the book chapter to see the reasoning.

**Extensible.** Fork or modify artifacts for your specific needs. These are starting points, not constraints.

---

## Connect

- **Book & Early Access:** [craftingplatforms.com](https://www.craftingplatforms.com)
- **Newsletter:** [newsletter.craftingplatforms.com](https://newsletter.craftingplatforms.com) — practical articles on platform engineering
- **GitHub:** [github.com/craftingplatforms](https://github.com/craftingplatforms)
- **Author:** Ezequiel Foncubierta — 25 years in infrastructure, cloud, and platform engineering

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
