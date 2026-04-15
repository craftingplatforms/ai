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
| 3 | Platform Notation |
| 4 | Segmentation |
| 5 | Identity and Access Management |
| 6 | Infrastructure |
| 7 | CI/CD |
| 8 | Observability |
| 9 | Security and Compliance |
| 10 | Developer Experience |

Artifacts tied to book chapters will be added as the book is completed. Community contributions grounded in platform engineering best practices are also welcome.

---

## Artifact Inventory

Skills are distributed as **Claude Code plugins**, grouped by cloud provider and domain.

### Plugin: `platform-design`

Platform strategy, segmentation, IAM design, and landing zone design.

| Skill | Chapter | Status |
|-------|---------|--------|
| [`define-platform-vision`](plugins/platform-design/skills/define-platform-vision/) | Chapter 2 | Published |
| [`design-segmentation`](plugins/platform-design/skills/design-segmentation/) | Chapter 4 | Published |
| [`define-core-iam`](plugins/platform-design/skills/define-core-iam/) | Chapter 5 | Published |
| [`define-tenant-iam`](plugins/platform-design/skills/define-tenant-iam/) | Chapter 5 | Published |
| [`design-landing-zone`](plugins/platform-design/skills/design-landing-zone/) | Chapter 6 | Published |
| [`define-naming-convention`](plugins/platform-design/skills/define-naming-convention/) | Chapter 6 | Published |
| [`design-networking`](plugins/platform-design/skills/design-networking/) | Chapter 6 | Published |
| [`design-compute`](plugins/platform-design/skills/design-compute/) | Chapter 6 | Published |

### Plugin: `aws`

AWS platform engineering — IAM, landing zones, and networking management.

| Skill | Chapter | Status |
|-------|---------|--------|
| [`manage-aws-iam`](plugins/aws/skills/manage-aws-iam/) | Chapter 5 | Published |
| [`manage-aws-landing-zone`](plugins/aws/skills/manage-aws-landing-zone/) | Chapter 6 | Published |
| [`manage-aws-networking`](plugins/aws/skills/manage-aws-networking/) | Chapter 6 | Published |

### Plugin: `azure`

Azure platform engineering — IAM, landing zones, and networking management.

| Skill | Chapter | Status |
|-------|---------|--------|
| [`manage-azure-iam`](plugins/azure/skills/manage-azure-iam/) | Chapter 5 | Published |
| [`manage-azure-landing-zone`](plugins/azure/skills/manage-azure-landing-zone/) | Chapter 6 | Published |
| [`manage-azure-networking`](plugins/azure/skills/manage-azure-networking/) | Chapter 6 | Published |

### Plugin: `gcp`

GCP platform engineering — IAM, landing zones, and networking management.

| Skill | Chapter | Status |
|-------|---------|--------|
| [`manage-gcp-iam`](plugins/gcp/skills/manage-gcp-iam/) | Chapter 5 | Published |
| [`manage-gcp-landing-zone`](plugins/gcp/skills/manage-gcp-landing-zone/) | Chapter 6 | Published |
| [`manage-gcp-networking`](plugins/gcp/skills/manage-gcp-networking/) | Chapter 6 | Published |

### Plugin: `kubernetes`

Kubernetes platform engineering — IAM and namespace management.

| Skill | Chapter | Status |
|-------|---------|--------|
| [`manage-k8s-iam`](plugins/kubernetes/skills/manage-k8s-iam/) | Chapter 5 | Published |
| [`manage-k8s-namespaces`](plugins/kubernetes/skills/manage-k8s-namespaces/) | Chapter 6 | Published |

Subscribe to the [newsletter](https://newsletter.craftingplatforms.com) for announcements when new artifacts are released.

---

## Project Structure

```
ai/
├── .claude-plugin/  # Marketplace catalog (marketplace.json)
├── plugins/         # Plugins grouped by cloud provider / domain
│   ├── aws/         #   AWS skills + plugin manifest
│   ├── azure/       #   Azure skills + plugin manifest
│   ├── gcp/         #   GCP skills + plugin manifest
│   ├── kubernetes/  #   Kubernetes skills + plugin manifest
│   └── platform-design/ # Platform design skills + plugin manifest
├── references/      # Shared notation and types (symlinked into each plugin)
├── .claude/         # Claude Code operational configs (internal)
├── CONTRIBUTING.md  # How to contribute
└── README.md        # This file
```

---

## Install Plugins

This repository is a [Claude Code Plugin Marketplace](https://code.claude.com/docs/en/plugin-marketplaces).

### Add the marketplace

```
/plugin marketplace add efoncubierta/craftingplatforms-ai
```

### Install individual plugins

```
/plugin install platform-design@crafting-platforms
/plugin install aws@crafting-platforms
/plugin install azure@crafting-platforms
/plugin install gcp@crafting-platforms
/plugin install kubernetes@crafting-platforms
```

Once installed, skills are available as slash commands — for example `/design-segmentation` or `/manage-aws-iam`.

Support for additional AI platforms (GitHub Copilot, Cursor, etc.) is planned for future releases.

---

## Contributing

Contributions are welcome — new artifacts, improvements to existing ones, and bug reports.

- **Guidelines and process:** [CONTRIBUTING.md](CONTRIBUTING.md)
- **Propose a new artifact:** [open an issue](.github/ISSUE_TEMPLATE/new-artifact.md)
- **Report a problem:** [open an issue](.github/ISSUE_TEMPLATE/bug-report.md)

### Artifact types

| Type | Location | Details |
|------|----------|---------|
| Plugin | [`plugins/`](plugins/) | Groups related skills; each has a `plugin.json` manifest |
| Skill | `plugins/<plugin>/skills/` | Reusable task guidance — design, implementation, or hybrid |

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
