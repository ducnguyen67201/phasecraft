# Phasecraft

**Coordinator-led agent engineering.**

A practical skill and playbook for delivering engineering work across separate agent conversations.

- **Human:** sets goals, permissions, and approval policy.
- **Coordinator:** tracks scope, owners, dependencies, and next actions.
- **Phase owners:** implement, integrate, review, verify, and request required approvals.

The hierarchy defines responsibility. The dependency graph determines what can run in parallel and what must wait.

## Get started

1. Follow the [quickstart](docs/guides/quickstart.md).
2. Use the [coordinator skill](skills/phase-coordinator/SKILL.md) and [templates](templates/).
3. Start with one coordinator and a few owners in separate workspaces.

[Operating procedure](docs/guides/operating-procedure.md) · [Worked example](examples/sample-project/)

## Explore

[Write-up](docs/articles/engineering-with-phase-owners.md) · [Architecture](docs/architecture/workflow.md) · [Memory and federation proposal](docs/architecture/memory-and-federation.md)

Today: a skill and documentation kit. Multiple coordinators and Obsidian/RAG integration are proposed extensions.

Inspired by [ECC](https://github.com/affaan-m/ecc); an independent project.

[MIT license](LICENSE) · [Contribute](CONTRIBUTING.md) · [Sources](docs/sources.md) · [Validation](docs/validation.md)
