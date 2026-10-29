# [PHASE-ID] — [Outcome]

## Assignment

- Status: STAGED until an authorized dispatch is recorded.
- Owner/session: [owner and session ID]
- Coordinator/reporting destination: [ID or channel]
- Workspace/branch/base: [isolated checkout, branch, verified base]
- Authorization source: [human/project source for this scope and coordination]

## Outcome and boundaries

[One observable delivery the human can assess.]

- In scope: [bounded work]
- Excluded: [adjacent work that is not dispatched]
- Owned surfaces: [files/modules/interfaces]
- Canonical shared contract producer: [owner/artifact]

## Dependency gates

| Gate        | Predecessor/artifact                      | Required evidence           | Independent work allowed now |
| ----------- | ----------------------------------------- | --------------------------- | ---------------------------- |
| Execution   | [input or none]                           | [proof]                     | [scope]                      |
| Integration | [actual source/contract]                  | [version/hash/behavior]     | [scope]                      |
| Publication | [merged predecessor or accepted artifact] | [verified merge/acceptance] | [scope]                      |

## Verification and acceptance

- Required checks/manual flows: [project policy and relevant behavior]
- Known evidence limits: [fixtures/local/provider/deployment distinctions]
- Acceptance criteria and authority: [observable facts and reviewer]
- Design/publication/merge/deployment gates: [separate actions and sources]
- Resource/cleanup responsibility: [owned resources; preservation limits]

## Owner direction

You own implementation, safe integration in your workspace, review, checks, resolving findings, direct approval requests, and specifically approved publication. Do not wait for duplicate coordinator execution or review. Report status, exact dependency evidence, and your next action. Do not expand scope, invent upstream services, change another owner's checkout, or dispatch successors.
