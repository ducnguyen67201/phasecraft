# Phasecraft

**A practical operating procedure for coordinator-led agent engineering.**

A human sets the goal and authority, a coordinator maintains the delivery map, and accountable phase owners carry bounded work through implementation and delivery. Run independent work in parallel and keep decisions, dependencies, and evidence outside any one conversation.

Phasecraft packages a workflow developed during a real engineering project. Version 0.1 is a skill and documentation kit: a procedure to use with your coding assistant and existing Git tooling. The single-coordinator approach has been used in practice; multi-coordinator operation and retrieval-backed memory are design proposals, not implemented capabilities. No comparative performance study has been conducted.

## Start here

1. Read the [quickstart](docs/guides/quickstart.md) and choose your project's approval and verification policy.
2. Use the [Phase Coordinator skill](skills/phase-coordinator/SKILL.md) to write phase briefs and a registry.
3. Give each active owner a separate workspace, bounded authority, and real dependency artifacts.
4. Follow the [operating procedure](docs/guides/operating-procedure.md) through review, approval, merge, and retirement.

Start with one coordinator and two or three phase owners. Increase concurrency when interfaces and workspace ownership are clear.

## How it works

The **human** sets the outcome, authority, and approval policy. The **coordinator** maintains the map: scope, ownership, dependencies, approvals, and next actions. Each **phase owner** implements its work, integrates its branch, reviews and verifies the result, requests any required human approvals, and performs approved publication and merge actions.

The coordinator needs a reliable map, not every implementation detail in its context window. Detailed investigation stays with the owner; durable handoffs carry what successors need.

### Hierarchy assigns responsibility; the graph determines readiness

Coordinator-led agent engineering uses two structures together:

| Structure               | What it describes                                                                                                                                                      |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Ownership hierarchy** | The human sets policy, the coordinator delegates and tracks work, and phase owners deliver their assigned outcomes. Owners request required human approvals directly.  |
| **Dependency graph**    | Phases depend on specific artifacts and evidence. Separate edges govern when implementation can start, when integration is possible, and when publication can proceed. |

Sharing a coordinator does not make phases sequential. For example, an API owner and a screen owner can work concurrently from a frozen contract. The screen owner can prepare its preview immediately, but final integration needs the actual API, and publication waits for its verified merge when that dependency is required. Phase numbering and reporting relationships do not create technical dependencies.

The hierarchy keeps accountability clear; the dependency graph makes useful parallelism visible. Both are maintained through project records and owner handoffs.

![Single-coordinator engineering workflow](docs/diagrams/phase-ownership-architecture.svg)

[Diagram context and editable source](docs/architecture/workflow.md)

## What is included

| Resource                                                                     | Purpose                                                                    |
| ---------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| [Portable skill](skills/phase-coordinator/SKILL.md)                          | Decision rules for a coordinating assistant                                |
| [Operating procedure](docs/guides/operating-procedure.md)                    | A repeatable delivery process for engineers                                |
| [Templates](templates/)                                                      | Project policy, briefs, handoffs, approvals, and registry schema           |
| [Worked example](examples/sample-project/)                                   | A fictional dependency graph with separate execution and publication gates |
| [Write-up](docs/articles/engineering-with-phase-owners.md)                   | Why the workflow took this shape and where it can fail                     |
| [Memory and federation proposal](docs/architecture/memory-and-federation.md) | A path toward multiple coordinators, Obsidian, and retrieval               |

The instructions are plain Markdown and JSON. They can be adapted to other assistants, but tool names, skill discovery, chat permissions, worktree handling, and monitoring must be mapped to the host you actually use. This repository does not claim tested feature parity across assistants.

## Rules that make parallel work useful

- Assign one accountable owner to a phase and one implementation writer to a checkout.
- Separate work that can start now from integration and publication that require an actual merged predecessor.
- Use canonical shared contracts and exact, reviewed checkpoints. Do not invent duplicate interfaces to appear unblocked.
- Keep authorization and evidence explicit. A fixture, a build, and a genuine integrated flow establish different facts.
- Let owners finish their own review and checks; do not add a duplicate coordinator gate.
- Verify an actual repository merge before releasing merge-gated dependents. Retire the merged owner from monitoring and route later fixes to an active or newly authorized owner.
- Keep acceptance, retirement, deletion, runtime cleanup, and deployment as separate decisions.

Testing policy, UI/design gates, publication authority, deployment permissions, and monitoring cadence belong to the adopting project. The templates help you choose them; a skill does not grant authority.

## Relationship to ECC

[ECC](https://github.com/affaan-m/ecc) is an inspiration for distributing reusable agent engineering practices. Phasecraft focuses on the delivery procedure between a human, a coordinator, and phase owners. It can be used alongside an existing toolbox. It is independent of ECC and is not an official ECC extension.

The current source is original project material; this package does not vendor ECC agents, hooks, installers, or skills. See [sources and provenance](docs/sources.md) and [initial validation](docs/validation.md).

## Contribute

Bring concrete failure cases, small improvements, and evidence of how the procedure behaves. See [CONTRIBUTING.md](CONTRIBUTING.md).

Licensed under [MIT](LICENSE).
