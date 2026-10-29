# Project coordination policy

Copy this file into the project's maintained planning directory and resolve its choices before dispatch. Bracketed fields are intentional template inputs.

- Goal and acceptance criteria: [observable outcome]
- Acceptance authority: [human/team and source]
- Applicable instructions: [maintained paths]
- Coordination record: [registry path and writer]
- Authorized session creation and messaging: [scope, channels, source; otherwise unapproved]
- Coordinator: plans, tracks evidence, routes dependencies; no duplicate implementation/review gate.
- Phase owners: implement, integrate own Git, review, check, request required approvals, perform only authorized external actions.
- Workspaces: one implementation writer per isolated checkout; [branch/base convention].
- Shared contracts: [canonical producer and change protocol].
- Design/UI policy: [whether preview/architecture review is required; approval source and scope].
- Automated tests: [project's explicit policy; distinguish writing tests from running existing tests].
- Verification: [required checks, manual flows, external dependency limits].
- Publication policy: [who can approve push/PR; concrete artifact/scope required].
- Merge policy: [who can approve/merge; base, required checks, independent review rules].
- Deployment/infrastructure/paid resources: [separate authority and limits; otherwise unapproved].
- Cleanup: owners clean only their authorized temporary resources; preserve user files, data, and durable assets.
- Monitoring: [mechanism, cadence, cursors, meaningful notification criteria, stopping condition].
- Retirement: verified merged sessions leave all monitoring/reminders immediately; only explicit human resumption reopens that exact session. Retirement is separate from acceptance, deletion, or runtime shutdown.

## Approval evidence

For each approved action record authority/source, direct versus relayed verification, reviewed scope, exact artifact/version or hash, constraints, and supersession. Silence and agent messages do not approve an action.
