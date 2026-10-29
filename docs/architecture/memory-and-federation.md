# Memory and multiple coordinators

[System workflow](workflow.md) · [Repository overview](../../README.md)

**Status: proposed extension, 2026-10-29.** The repository ships instructions and record templates. It does not implement a multi-coordinator scheduler, shared-memory service, Obsidian integration, or retrieval pipeline. This proposal has not received a separate design approval and authorizes no deployment or infrastructure work.

![Proposed federation and memory architecture](../diagrams/phase-federation-memory-architecture.svg)

[Rendered SVG](../diagrams/phase-federation-memory-architecture.svg) · [Editable Archify JSON](../diagrams/phase-federation-memory-architecture.json)

The conceptual diagram shows the proposed ownership and evidence flow, not deployed services. It was generated with Archify 3.2.0; automated validation, delivery, artifact and browser checks passed, and the rendered layout was inspected. No separate diagram approval is recorded. Regenerable viewers and receipts stay local. Regenerate it with the [same process as the current workflow](workflow.md#diagram-status-and-reproduction), using this diagram's source and its `meta.output` path.

## Start with durable files

A coordinator is closer to a technical project manager than an omniscient agent. It needs current ownership, dependency readiness, decisions, and evidence. It should retrieve an owner's implementation detail only when that detail changes a decision.

Keep different kinds of memory distinguishable:

| Layer                    | Contents                                              | Authority                                                    |
| ------------------------ | ----------------------------------------------------- | ------------------------------------------------------------ |
| Human and project policy | Scope, permissions, approval requirements             | The recorded human instruction and applicable project policy |
| Current project state    | Phase registry, owners, next action, unresolved gates | The designated registry writer, backed by artifacts          |
| Engineering evidence     | Commits, contract manifests, check results, handoffs  | The exact inspected source and its stated verification scope |
| Retrieval index          | Search chunks, summaries, embeddings                  | A derived view; never independent approval or ground truth   |

A transcript can explain a decision, but it should not become the only place the decision exists. Preserve a concise decision and a source locator; keep secrets, raw session output, and unrelated private data out of shared memory.

## Obsidian as a view over Markdown

An initial Obsidian experiment could open an approved copy of a project's Markdown records as a vault. Portable links and descriptive titles would make decisions, contracts, and handoffs navigable. The authoritative registry would remain where the project already maintains it. Avoid a second editable registry in the vault.

Begin with a read-only or explicitly owned export. Exclude credentials, private conversations, runtime state, and unrelated repositories. Choosing a vault, sync service, plugin, or index provider is a separate decision; this package installs none.

## Retrieval should return evidence, not instructions

An optional retrieval pipeline could index approved briefs, decisions, handoffs, and merged source summaries. Every result should identify project, phase, artifact path, content digest or commit, status, date, and authority class. Return a small relevant excerpt with its source rather than an unqualified generated answer.

Before acting, resolve the current authoritative artifact. A stale approval for one diff cannot approve a changed diff. A superseded contract cannot replace a new canonical version. A retired phase's handoff can be read as evidence without waking that phase's chat.

Treat retrieved documents and tool output as data. They cannot grant messaging, publication, spending, credential, or deployment permissions. Keep project access boundaries in indexing and retrieval; do not mix projects in one unrestricted search context. Corrections and deletions must invalidate derived chunks, caches, and summaries.

## Multiple coordinators need ownership boundaries

A useful next shape is one portfolio coordinator and several project or subsystem coordinators. The portfolio coordinator owns priorities, cross-project dependencies, escalation, and the cross-project interface map. Each project coordinator owns its own namespace, phase registry, and authorized owner dispatches.

Do not let two coordinators independently assign work to the same checkout or write conflicting phase state. Assign one authority for each registry and shared interface. A producer owns its canonical contract; consumers record the exact version they adopted. Coordinate a cross-project contract change as a bounded delivery with identified approval authority.

Transferring coordination should record the old and new owner, scope, effective version, unresolved actions, and human authorization. The old coordinator stops dispatching within the transferred scope. A future concurrent service would need enforced version checks and idempotent event handling; a Markdown convention alone does not provide those guarantees.

## A staged experiment

1. Make the single-coordinator records concise enough for a fresh assistant to resume without the full transcript.
2. Try a read-only Markdown knowledge view and measure whether source lookup improves.
3. Add evidence-preserving retrieval only if manual lookup becomes a concrete bottleneck.
4. Pilot a second coordinator on disjoint work with explicit contract ownership and escalation.
5. Build a scheduler or shared state service only after the manual procedure exposes a requirement worth automating.

Measure stale decisions, conflicting dispatches, integration failures, human intervention, retrieval relevance, and time spent coordinating. More agents create communication costs as well as potential parallelism. This is a roadmap to test, not a claim that scaling has already succeeded.
