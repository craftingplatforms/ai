# GitHub Copilot — Platform Engineer Instructions

> Place this file as `.github/copilot-instructions.md` in your platform repository.

## Context

This is a **platform engineering repository**. The code here builds and operates an internal developer platform used by product teams in our organization.

Key conventions:
- Infrastructure is managed with Terraform (HCL). Use `go` syntax highlighting in Markdown code blocks for HCL.
- Kubernetes manifests use YAML. Always include resource limits and labels.
- All resources must have the standard tags: `Platform`, `Environment`, `Team`, `ManagedBy`, `CostCenter`.
- No hardcoded credentials, IPs, or environment-specific values — use variables and references.
- CI/CD uses OIDC for cloud authentication. Never suggest long-lived credentials.

## When Writing Terraform

- Use explicit provider and module version constraints
- Include `description` on all variables
- Prefer data sources over hardcoded resource IDs
- Group related resources into modules only when the pattern repeats 3+ times

## When Writing CI/CD Pipelines

- Require OIDC authentication for cloud provider access
- Security scanning (SAST, container scan) must run before any deploy step
- Production deployments require a manual approval gate
- Always pin action versions to full SHA (not floating tags)

## When Writing Kubernetes Manifests

- Always set resource requests and limits
- Use `readOnlyRootFilesystem: true` where possible
- Never use `hostNetwork` or `privileged` without a comment explaining why
- Labels must include: `app`, `version`, `team`, `managed-by`

## Related Book

These conventions are explained in depth in *Crafting Platforms* by Ezequiel Foncubierta — [craftingplatforms.com](https://www.craftingplatforms.com).
