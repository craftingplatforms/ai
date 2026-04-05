# Crafting Platforms — AI Artifacts

Build and train AI agents to architect internal developer platforms. This repository contains reusable skills, commands, agents, and configurations for major AI platforms (Claude Code, GitHub Copilot, Cursor). Closely related to the [**Crafting Platforms**](https://craftingplatforms.com) book — but open to any platform engineering or AI best practice.

## What Is This?

Instead of manually architecting your platform, **teach an AI agent to do it**. This repository provides pre-built, production-ready artifacts that guide AI through platform engineering tasks: designing segmentation strategies, scaffolding infrastructure, auditing security, automating CI/CD, and more.

Many artifacts here relate to chapters in *Crafting Platforms*, bridging human guidance (the book) and machine execution (the code). Others are grounded in platform engineering or AI best practices — the repository grows with the community.

---

## The Book: Crafting Platforms

**By Ezequiel Foncubierta**

A practical guide to building opinionated, made-to-measure internal developer platforms that fit your organization's unique DNA.

> Platform craftsmanship, not platform manufacturing.

The book teaches **humans** the principles and patterns for building platforms. This repository teaches **AI agents** how to implement them. Together, they form a complete system: strategic guidance for people, executable instructions for machines.

### Get the Book

- **Website**: [craftingplatforms.com](https://www.craftingplatforms.com) — project home, about the author, and links
- **Early Access** (digital): [leanpub.com/crafting-platforms](https://leanpub.com/crafting-platforms) — get chapters as they're published
- **Newsletter**: [newsletter.craftingplatforms.com](https://newsletter.craftingplatforms.com) — practical articles, platform engineering insights, and early announcements

### Book Chapters

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

Artifacts tied to book chapters will be added as the book is completed. Community contributions grounded in platform engineering best practices are also welcome.

---

## Artifact Inventory

### Skills

| Skill | Chapter | Status |
|-------|---------|--------|
| [`define-platform-vision`](skills/define-platform-vision/) | Chapter 2 | Published |
| [`design-segmentation`](skills/design-segmentation/) | Chapter 3 | Published |
| [`define-core-iam`](skills/define-core-iam/) | Chapter 4 | Published |
| [`define-tenant-iam`](skills/define-tenant-iam/) | Chapter 4 | Published |
| [`manage-azure-iam`](skills/manage-azure-iam/) | Chapter 4 | Published |
| [`manage-aws-iam`](skills/manage-aws-iam/) | Chapter 4 | Published |
| [`manage-gcp-iam`](skills/manage-gcp-iam/) | Chapter 4 | Published |
| [`manage-k8s-iam`](skills/manage-k8s-iam/) | Chapter 4 | Published |
| [`design-landing-zone`](skills/design-landing-zone/) | Chapter 5 | Published |
| [`define-naming-convention`](skills/define-naming-convention/) | Chapter 5 | Published |
| [`design-networking`](skills/design-networking/) | Chapter 5 | Published |
| [`design-compute`](skills/design-compute/) | Chapter 5 | Published |
| [`manage-azure-landing-zone`](skills/manage-azure-landing-zone/) | Chapter 5 | Published |
| [`manage-aws-landing-zone`](skills/manage-aws-landing-zone/) | Chapter 5 | Published |
| [`manage-gcp-landing-zone`](skills/manage-gcp-landing-zone/) | Chapter 5 | Published |
| [`manage-azure-networking`](skills/manage-azure-networking/) | Chapter 5 | Published |
| [`manage-aws-networking`](skills/manage-aws-networking/) | Chapter 5 | Published |
| [`manage-gcp-networking`](skills/manage-gcp-networking/) | Chapter 5 | Published |
| [`manage-k8s-namespaces`](skills/manage-k8s-namespaces/) | Chapter 5 | Published |

Subscribe to the [newsletter](https://newsletter.craftingplatforms.com) for announcements when new artifacts are released.

---

## Project Structure

```
ai/
├── skills/          # Reusable AI skills (one per task)
├── commands/        # Chat/slash commands (workflows)
├── agents/          # Specialized agent definitions
├── hooks/           # Event-driven automation scripts
├── mcp/             # Model Context Protocol servers
├── .claude/         # Claude Code operational configs (internal)
├── CONTRIBUTING.md  # How to contribute
└── README.md        # This file
```

---

## Install Artifacts

### Claude Code

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

---

## Contributing

Contributions are welcome — new artifacts, improvements to existing ones, and bug reports.

- **Guidelines and process:** [CONTRIBUTING.md](CONTRIBUTING.md)
- **Propose a new artifact:** [open an issue](.github/ISSUE_TEMPLATE/new-artifact.md)
- **Report a problem:** [open an issue](.github/ISSUE_TEMPLATE/bug-report.md)

### Artifact types

| Type | Directory | Details |
|------|-----------|---------|
| Skill | [`skills/`](skills/README.md) | Reusable task guidance — design, implementation, or hybrid |
| Command | [`commands/`](commands/README.md) | Named slash-command workflows |
| Agent | [`agents/`](agents/README.md) | Specialized sub-agents with narrow scope |
| Hook | [`hooks/`](hooks/README.md) | Event-driven automation scripts |
| MCP server | [`mcp/`](mcp/README.md) | Domain-specific tool extensions |

---

## Philosophy

**Opinionated.** Platforms should be tailored to your org, built with clear principles, and designed for team autonomy.

**Practical.** Every artifact is grounded in real-world platform engineering. No toy examples.

**Transparent.** You should understand why an artifact makes the recommendations it does — read the source and, where linked, the book chapter behind it.

**Extensible.** Fork or modify artifacts for your needs. These are starting points, not constraints.

---

## Connect

- **Website:** [craftingplatforms.com](https://www.craftingplatforms.com)
- **Early Access:** [leanpub.com/crafting-platforms](https://leanpub.com/crafting-platforms)
- **Newsletter:** [newsletter.craftingplatforms.com](https://newsletter.craftingplatforms.com)
- **GitHub:** [github.com/craftingplatforms](https://github.com/craftingplatforms)
- **Author:** Ezequiel Foncubierta — [foncubierta.com](https://foncubierta.com) · [@foncubierta.com](https://bsky.app/profile/foncubierta.com) on Bluesky

---

## License

Apache 2.0 — see [LICENSE](LICENSE) for details.

---

**Build the platform your org deserves. Start with the book, execute with the code.**
