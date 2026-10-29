# Record contracts

Use existing project records when they already carry these facts. These are portable field guides, not a mandate for a database, host tool, or fixed number of phases.

## Project policy

Record the goal, acceptance authority, applicable instructions, coordinator and owner responsibilities, authorized messaging, workspace isolation, test policy, design/UI review policy, publication and merge authority, deployment/infrastructure permissions, cleanup ownership, and monitoring stop condition. Mark unknown permission as unknown. A default recommendation is not approval.

## Phase brief

Include an immutable phase ID, title, measurable outcome, in-scope and excluded work, owner/session/workspace/branch, owned surfaces and shared contract producer, execution/integration/publication gates, checks and evidence limits, required approval actions, acceptance criteria, and reporting destination. A dispatch changes authorization state; editing a future brief alone does not dispatch it.

## Registry

Keep one authority for current coordination state and a writer for each record. Store:

- Stable phase and owner/session IDs; workspace and branch; brief and handoff paths.
- Lifecycle status (`STAGED`, `RUNNING`, `READY_FOR_REVIEW`, `AWAITING_APPROVAL`, `PR_OPEN`, `MERGED`, `COMPLETE`), plus separate `waitReason`, merge evidence, acceptance, and retirement.
- Dependency edges with `gate` (`execution`, `integration`, or `publication`), predecessor ID, required artifact, and evidence of satisfaction.
- Shared checkpoints: producer, frozen/merged state, paths, versions or hashes, consumer verification, and limitations.
- Approval references, exact PR URL/head/base, actual merge timestamp/commit and verifier, monitoring enabled/cursor, next action, and resource ownership.

`COMPLETE` requires the project's acceptance criteria and delivery artifact, not an idle session. `MERGED` can still await acceptance. A merged session is retired even if a different active owner must finish acceptance work. Do not reactivate it implicitly.

## Approval record

Use an action such as `design`, `publish`, `merge`, `deploy`, or `infrastructure`; the authority and source location; direct verification versus owner relay; timestamp if known; exact scope and artifact identity; constraints; and any superseded approval. Null means unknown, not approved. Preserve the original approval source rather than rewriting it into a stronger instruction.

## Checkpoint

Record the producing phase, contract name/version, relative file manifest with a digest algorithm and exact hash per file, behavior/error/transaction semantics, consumers, freeze time, and known limits. Clearly distinguish a reviewed frozen packet from actual merged source. Never include secrets or raw private command output.

## Handoff

Lead with outcome/status and next action. Record completed scope and exclusions, actual base/head/diff, checks performed and their limitations, required interfaces and consumer instructions, approval sources, PR/merge facts, acceptance status, owned resource state, cleanup performed, and durable evidence links. State what successors can rely on without reopening the owner session.
