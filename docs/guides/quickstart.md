# Run your first coordinated project

[Back to Phasecraft](../../README.md)

Use this kit with an engineering repository and an assistant that can read files. Separate persistent chats and isolated workspaces make parallel implementation easier. If those capabilities are unavailable, use the same records and run phases sequentially.

## 1. Choose the project policy

Copy [project-policy.md](../../templates/project-policy.md) into your engineering repository, normally under `docs/phases/`. Decide who can create or message chats, start implementation, change shared interfaces, add tests, publish branches and PRs, merge, deploy, and spend money. Record the human instruction that grants authority. Existing repository rules still apply.

Pick meaningful verification for your product. Some teams require automated tests; others reserve test authoring for a separate owner. Do not silently import a preference from the example project.

## 2. Give the coordinator a bounded request

Use a prompt like this, replacing the scope and policy:

> Use the Phase Coordinator skill. Plan the account settings feature as small reviewable phases. You coordinate the registry, dependencies, and handoffs. Phase owners implement, integrate, review, verify, and request approvals. Propose separate chats and workspaces; create or message them only within my recorded authorization. Follow docs/phases/project-policy.md. Do not take over implementation unless I ask.

Planning alone does not authorize background monitoring or external publication. If you want those, state the bounded authority and completion condition.

## 3. Install the skill where your host discovers it

The portable unit is the complete `skills/phase-coordinator/` directory, including its references. For a Codex setup that uses `~/.codex/skills`, inspect it and copy it into an unused destination:

```sh
test ! -e "$HOME/.codex/skills/phase-coordinator" &&   mkdir -p "$HOME/.codex/skills" &&   cp -R skills/phase-coordinator "$HOME/.codex/skills/phase-coordinator"
```

Run that command from this repository. If the destination already exists, compare it manually and choose which version to keep. Do not overwrite an existing skill or layer two versions automatically. Use your host's documented reload/discovery mechanism, then invoke `$phase-coordinator` or provide its file as instructions.

Other hosts can read the Markdown, but discovery paths and tool permissions vary. No plugin installer or cross-host adapter is included.

## 4. Create records and dispatch owners

Start from the [sample project](../../examples/sample-project/registry.json) and [phase brief](../../templates/phase-brief.md). Resolve independent work, exact shared interfaces, integration edges, and publication edges. Record one owner, chat, workspace, and branch for each active phase.

Each dispatch says who owns implementation, integration, review, checks, approval requests, and specifically approved publication. An owner reports a concise milestone instead of sending its full debugging history to the coordinator.

## 5. Finish one delivery before expanding

Have an owner exercise the main behavior and relevant failure paths, run the selected checks, present the concrete change and limitations, and obtain the required approvals. Verify actual merge metadata before using it as a dependency gate. Record acceptance separately. Retire the merged chat, preserve its handoff, and assign future follow-ups to a current owner.

Then review whether coordination helped. Track elapsed time, human interventions, integration conflicts, duplicate work, monitoring cost, and escaped defects before claiming an improvement.

Continue with the [full procedure](operating-procedure.md) and the [write-up](../articles/engineering-with-phase-owners.md).
