# Initial package validation

[Repository overview](../README.md)

Checked on 2026-10-29 for the initial documentation and skill package.

- Skill Creator's structural validator accepted the portable skill and metadata.
- The registry schema is valid JSON Schema Draft 2020-12. The fictional registry and pending approval template validate against their relevant schema definitions.
- Invalid variants covering merged-but-monitored state, completion without acceptance, and approval without a source were rejected during local validation.
- JSON parses, local Markdown links resolve, and the example contract's SHA-256 matches its manifest. Example approval references resolve to fictional source events.
- Archify validation, delivery, artifact and browser gates passed for both diagrams. The rendered layouts were inspected. Canonical SVG exports parse and contain no scripts or personal local paths.
- An independent assistant applied the skill to synthetic release cases: an open PR with a prospective merge commit, a downstream frozen-contract consumer, a merged owner awaiting acceptance with a running server, a changed design, and two owners sharing a checkout. The design case needed a correction: the evaluator initially assumed a preimplementation UI gate absent from the supplied policy. Rereading the skill restored the project-specific policy. This is a bounded behavioral exercise, not a live release or benchmark.

These checks do not establish orchestration runtime behavior, cross-assistant compatibility, retrieval quality, team productivity improvements, or correctness for every project. The package contains no runtime implementation. Applying it requires the adopting project's policies, real tools, and judgment.

The registry schema checks record structure and a few local invariants. It cannot authenticate a human approval, prove a GitHub merge, enforce exclusive worktree ownership, or validate every cross-record dependency. Resolve those facts from their actual sources.
