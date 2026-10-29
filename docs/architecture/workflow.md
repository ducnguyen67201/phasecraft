# Coordinator and phase ownership

[Project overview](../../README.md) · [Operating procedure](../guides/operating-procedure.md) · [Proposed memory and federation](memory-and-federation.md)

This diagram describes the single-coordinator procedure practiced during development and generalized for Phasecraft. It models people, agent responsibilities and durable evidence; the boxes are not deployed services. Phasecraft ships documentation, a skill and templates, with no orchestration runtime.

![Coordinator and phase ownership](../diagrams/phase-ownership-architecture.svg)

[Rendered SVG](../diagrams/phase-ownership-architecture.svg) · [Editable Archify JSON](../diagrams/phase-ownership-architecture.json)

## Responsibilities and authority

The human sets scope and project policy, including which design, publication and merge actions require direct approval. The coordinator keeps the dependency map and registry, dispatches authorized work and verifies repository merge metadata. It does not need every implementation detail and does not repeat the owner's execution or review.

Each phase owner works in an isolated workspace, integrates its own branch, reviews and checks its work, presents concrete results, requests required approvals directly and performs only authorized external actions. Briefs, handoffs and exact contract checkpoints make information portable across contexts.

Repository files and tool results are evidence. They do not grant permission or replace the human's approval. A frozen dependency checkpoint can support independent implementation; publication dependencies still require the agreed actual merged source.

After an actual merge is verified, the coordinator retires that owner chat from monitoring and reminders. Later work goes to a current or newly authorized owner. Retirement does not establish acceptance, delete worktrees or stop runtimes.

## Diagram status and reproduction

Prepared on 2026-10-29 as documentation of the practiced procedure. No separate human approval of this diagram is recorded. Publishing this documentation does not implement the proposed federation or memory extensions.

The source was rendered with Archify 3.2.0. Showcase validation, delivery, artifact checks and browser checks passed; the rendered layout was also inspected. The SVG was produced through the viewer's canonical SVG export, with viewer state excluded. The editable JSON and SVG are durable source assets. Regenerable HTML viewers, delivery receipts and review captures remain local and ignored.

To regenerate with an installed Archify checkout, run from the repository root, replacing `ARCHIFY_CLI` with its CLI path:

```sh
node "$ARCHIFY_CLI" finalize architecture \
  docs/diagrams/phase-ownership-architecture.json \
  .archify/architecture-phase-ownership-20261029-123000/phase-ownership-architecture.html \
  --quality showcase --json
```

Open the generated viewer and choose **Export → SVG · Auto** to regenerate the SVG. A later render at an existing output path may need a fresh `--out-dir` for browser receipts. Keep conceptual responsibilities and labels intact when changing the layout.
