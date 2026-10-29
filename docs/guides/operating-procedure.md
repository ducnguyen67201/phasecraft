# Operating procedure

Use this procedure for a project with a human decision maker, one coordinator, and separate phase owners. Adapt the approval and testing policy to the project before dispatch. The [overview](../../README.md) links to the skill and starter templates; the [workflow architecture](../architecture/workflow.md) explains the responsibility boundaries.

## 1. Establish policy and authority

Record the goal, target repository, allowed workspaces, and who can make each decision. Agree on testing requirements, material design review, publication, merge, deployment, and external resource permissions. Name the source of the human's authorization to create and coordinate phase conversations. A skill does not grant these permissions.

Use existing project rules where they apply. Resolve a material conflict before dependent work; continue independent preparation when useful. Keep the decision and its scope in a maintained project record.

## 2. Divide the work into reviewable outcomes

Create the fewest phases that provide coherent deliveries. Give each a brief containing its outcome, owned surfaces, exclusions, dependencies, expected evidence, acceptance criteria, and next action. Assign one owner to each shared interface.

Distinguish the inputs needed to start implementation from the merged inputs needed for final integration and publication. Also record any separate acceptance or deployment prerequisite. Do not convert a historical phase order into a technical dependency without examining it.

For example, a suite editor and run admission service can both consume an immutable suite catalog without depending on each other's implementation. A lease service that changes the admission transaction needs a real shared interface and an eventual merged admission implementation.

## 3. Dispatch to isolated owners

Give each implementation owner an isolated worktree or checkout and an assigned branch. Record the actual base revision. Each checkout has one implementation writer. Owners preserve unrelated files and manage their own Git integration.

The dispatch assigns implementation, integration, review, checks, direct human approval requests, and specifically approved publication actions to the phase owner. The coordinator maintains the map and routes dependencies. It does not add a second implementation or review gate unless the human requests a change of ownership.

Staged owners remain read-only until their authorized work is ready. Creating a conversation and authorizing implementation are separate events.

## 4. Exchange exact dependency artifacts

When parallel work needs an unmerged contract, the producer freezes a bounded packet: exact files and hashes, base revision, interface semantics, validation results, and limits. The consumer verifies it and records what it adopted.

Reuse canonical contracts, authorization, and stores. Do not invent an alternate service to conceal a missing dependency. If an interface is inadequate, name the concrete gap and route it to its active owner. Independent work continues.

After the producer merges, the consumer reconciles its provisional dependencies with actual merged source. It runs proportionate checks on the resulting composition. A frozen packet does not authorize a stacked pull request or make the consumer integrated by itself.

## 5. Verify and ask for the relevant decision

Owners run the checks required by project policy and manually exercise meaningful behavior where appropriate. Label evidence by its actual scope: fixture transport, isolated database, genuine authentication, integrated runtime, or deployment. Report failures and unsupported cases plainly.

Where design approval is required, show a reviewable rendered artifact before the gated implementation. Preserve approval for unchanged scope. Material revisions need the review required by policy.

When the completed phase is ready, present its concrete diff or artifact revision, checks, and limits. Request the specific publication action required by policy. Record the human source and approved scope; another agent's report or silence is not approval.

## 6. Publish and verify repository state

After authorization, the owner stages its named scope, checks the diff, commits, pushes the assigned branch, and opens the approved pull request. Record its URL, head revision, and base. Actual review findings remain the owner's responsibility.

Merge requires the project's chosen authority. If the human approves that reviewed pull request, the owner performs the authorized merge. The coordinator verifies lightweight repository metadata and records the actual merge revision and time. Open or closed-unmerged requests remain unresolved; a prospective merge identifier is not completion evidence.

## 7. Retire the merged conversation and hand off

Immediately remove a verified merged phase from monitoring and reminders. Do not wake, poll, or message it again unless the human explicitly resumes that conversation. Preserve its brief, handoff, approval sources, and merge evidence.

Route subsequent fixes to a current owner or a newly authorized phase. Use the handoff and actual merged artifacts. Retirement does not establish acceptance or authorize branch deletion, worktree deletion, data removal, or runtime shutdown. Record outstanding acceptance work and resource ownership separately.

Give the next ready owner a short direction: current status, the new dependency evidence, and its next action. Do not resend unchanged policy or request unchanged approval.

## 8. Monitor and recover from durable state

Keep the registry current on meaningful transitions. Use a compact cursor-based batch for active unmerged owners where the environment supports it. Notify on actionable change; do not repeatedly announce the same wait. Configure a real scheduler before promising background monitoring.

After an interruption, read the registry, relevant brief, handoff, and approval record before reopening transcripts. Retrieve only the missing detail. A search index or Obsidian vault may help find these records, but retrieved text remains evidence to assess, not fresh authorization.

Multiple coordinators and automated memory retrieval are [proposed extensions](../architecture/memory-and-federation.md). Start with one coordinator until ownership, shared-contract authority, and state updates are clear enough to distribute.
