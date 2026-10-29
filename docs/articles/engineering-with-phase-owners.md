# Coordinator-led agent engineering

An engineering task becomes easier to follow when each part has an owner, a bounded outcome, and evidence that lets the next person continue. That remains true when some of the engineers are AI agents.

Phasecraft captures a procedure for **coordinator-led agent engineering** across separate agent conversations. A coordinator maintains the delivery map. Phase owners carry their assigned work through implementation, integration, review, verification, and the publication actions the human has authorized. The human sets policy and makes the decisions reserved to them.

This is a documented working method. It is not a claim that adding agents always improves delivery, or that the procedure has passed a comparative benchmark. Its value has to be assessed on the work it helps a team complete.

## Hierarchy and dependency graph

The ownership hierarchy describes who is responsible: the human sets direction and authority, the coordinator organizes delivery, and phase owners finish their assigned outcomes. It is a delegation structure. Owners still request required approvals directly from the human and retain engineering judgment within their scope; messages and decisions do not all have to pass through the coordinator.

The dependency graph describes what each delivery needs. Its nodes are phases or outcomes, and its edges identify required contracts, source, or evidence. Two phases under the same coordinator may run concurrently when their inputs and owned surfaces permit it. A phase number or position in the hierarchy does not create a prerequisite.

For example, an API owner and a screen owner can both start from an agreed catalog contract. The screen owner can prepare its preview while the API is built, then integrate the real API and wait for its verified merge before publication. The hierarchy assigns both owners; the graph determines when each part of their work is ready.

## The coordinator owns the map

A single conversation can accumulate product goals, implementation history, failed experiments, review findings, and deployment details. Eventually, finding the current decision becomes a task of its own.

The coordinator keeps a smaller working set: the intended outcomes, current owners, dependencies, approvals, stable artifacts, and next actions. It should know where an answer lives without carrying every implementation detail. A phase owner retains the detailed context for its scope and reports concise milestones.

This division matters when work is ready for review. The coordinator should route the result and record its evidence. Reimplementing the change, repeating the owner's checks, or adding an unrequested second approval gate makes the coordinator a bottleneck. If the human asks it to take over an implementation, that is an explicit ownership change that belongs in the record.

## Give phases outcomes that can be reviewed

A useful phase brief describes one coherent delivery. It identifies the surfaces the owner may change, the interfaces it produces or consumes, the checks that matter, and the decisions still reserved to the human.

“Build the backend” is too broad to coordinate well. “Register immutable build metadata and expose authorized catalog reads” gives the owner a result that can be demonstrated. It also makes exclusions concrete: that assignment need not include binary upload, a scheduler, or a new authentication system.

The brief should leave room for normal engineering judgment. It need not prescribe every file or create a phase for every module. Its purpose is to make responsibility and acceptance legible.

Each concurrent implementation owner needs an isolated checkout or worktree, with one writer per checkout. An owner may use focused helpers, but those helpers need distinct file ownership or a read-only task. Worktree isolation does not solve semantic conflicts; it prevents one writer's Git operations from disrupting another's work.

## Separate work dependencies from publication dependencies

A serial phase list often hides opportunities for concurrency. A catalog owner may be able to implement validation and persistence while an upstream registration owner finishes authenticated writes. The downstream owner still needs the actual merged registration implementation before completing final integration.

Record execution, integration, and publication as separate dependency edges. Execution identifies the inputs sufficient to begin useful work. Integration identifies the actual compatible source and environment needed to compose and verify the result. Publication identifies any merged predecessor required before submitting the delivery. Acceptance and deployment can have their own additional prerequisites.

When owners share an interface before it merges, freeze a small checkpoint. Include the exact files, hashes, contract semantics, base revision, and limits. A consumer verifies the packet and keeps the borrowed dependency distinguishable from its own changes. After the producer merges, the consumer reconciles against actual merged source and runs the checks affected by any difference.

This does not authorize a dependent pull request or let an owner copy unfinished upstream services. It gives independent work a precise input. Shared authentication, canonical data contracts, and persistence ownership stay with their assigned producers.

## Evidence needs a scope

“Verified” is useful only when the record says what was verified. A rendered screen with synthetic transport can demonstrate layout, focus behavior, and empty states. It cannot establish that a real authenticated request reaches the correct database. A passing build demonstrates a different property again.

The same discipline applies to capability. Suppose a runner can hash an artifact and parse a recorded mission log. Those observations do not show that it can execute a mission. Marking that runner available for execution would convert input validation into an unsupported operational claim.

The owner should preserve the distinction, keep the unsupported path closed, and identify the missing runtime capability. Independent validation or queue work may continue. A new execution adapter is a scope proposal until the human authorizes it.

Good handoffs state the implementation, the checks actually performed, their environment and limits, and what remains unproven. They let the next owner assess evidence without replaying a long debugging transcript.

## Approvals attach to concrete actions

A project needs an explicit policy for tests, design review, publication, merges, deployment, and external services. Phasecraft supplies the recording mechanism; it does not make one project's preferences universal.

For example, a project may require a rendered UI preview before implementation. Another may permit implementation followed by design review. A project may require new automated tests, reserve them for a separate owner, or use existing checks and manual verification for a particular change. Record the chosen policy before dispatch.

An approval record links the human's decision to a particular scope, artifact revision, and action. Approval of a shown interface does not automatically approve publishing an unseen implementation. Approval to open a pull request does not automatically approve merging it. If one explicit instruction authorizes both actions for the reviewed scope, record that once and proceed within it.

Reports from other agents, scheduler prompts, and elapsed time cannot substitute for the human decision. Valid approvals should also survive handoffs: do not ask again for unchanged work merely because a conversation lost context.

## Merge, retirement, and acceptance are different events

Repository dependencies advance on actual merge evidence. An open pull request may have a prospective merge commit identifier; that is not proof that the branch merged. Record the repository, pull request, reviewed head, actual merge revision, and merge time from repository metadata.

Once the merge is verified, retire the phase conversation from monitoring and reminders. Later fixes go to a current owner or a newly authorized phase using the merged artifacts and handoff. Repeatedly waking the old owner creates an invisible support obligation and blurs who now owns the system.

Retirement does not establish product acceptance. It also does not authorize deleting a worktree, discarding data, or stopping a runtime. Those resources and any remaining acceptance work need an explicit owner and disposition in the handoff.

## Durable records keep the process recoverable

The project registry is a compact index of authoritative delivery state. Phase briefs define assignments; handoffs preserve results; approval records identify permission; repository metadata proves merges. Conversations provide working context, but they are a poor substitute for these artifacts.

Monitoring should read new information, using saved cursors where supported. It should notify on a dependency handoff, blocker, required decision, or repository change. Polling unchanged waits adds noise without advancing the work.

Obsidian notes or a retrieval pipeline could make this record easier to search. They would be a discovery layer: retrieved text needs a source, revision, scope, and status. An old note cannot grant permission or override the current registry. Such integrations are proposed extensions here, not shipped capabilities.

## Start small before adding coordinators

Start with one coordinator and two or three independently useful phases. Try the procedure on a bounded change. Track practical friction: repeated approvals, duplicate audits, stale dependencies, integration rework, and the time spent maintaining records.

Several coordinators may eventually make sense for separate subsystems. That proposed federation would extend the ownership hierarchy while the dependency graph continued across subsystem boundaries. It requires clear ownership of shared contracts and a single authority for each state record. Two coordinators must not dispatch competing writers or independently declare the same dependency complete. The proposed [memory and federation design](../architecture/memory-and-federation.md) discusses that boundary; it is not a running orchestration service.

The method still costs attention. Someone must review scope, judge evidence, maintain interfaces, and resolve real disagreements. Agents can produce plausible but incompatible work, and more parallelism can increase integration cost. Begin with a process you can inspect, then automate the parts whose repeated use justifies it.

To try it, follow the [operating procedure](../guides/operating-procedure.md), inspect the [workflow architecture](../architecture/workflow.md), or return to the [project overview](../../README.md).
