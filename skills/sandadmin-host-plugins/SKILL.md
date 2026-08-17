---
name: sandadmin-host-plugins
description: Establish, change, release, or verify a SandAdmin PostgreSQL host and its optional Sand plugins. Use when initializing or taking over a SandAdmin repository, creating or changing a sand-* plugin, synchronizing a plugin into a host, preparing a plugin release, or assessing SandAI/SandIAM integration and lifecycle acceptance.
---

# SandAdmin Host and Plugins

Keep SandAdmin usable with zero business plugins while delivering plugins from an authoritative source workspace through a separately verified host.

## Completion standard

- Classify every changed capability and its authoritative repository before editing.
- Keep plugin source, host synchronization, and host acceptance as separate evidence-bearing stages.
- Report what was changed, checked, verified, committed, deployed, and still unverified without conflating them.
- Preserve unrelated working-tree changes. Do not commit, push, migrate data, reload services, or delete files without the user's authorization.

## Start with the local contract

Before material changes, read the repository's `AGENTS.md`, `README.md`, `docs/repository-governance.md`, `docs/architecture.md`, and `docs/plugin-development.md` when present. Inspect branch and working-tree state before assigning ownership or editing.

Apply `sand-platform-conventions` before choosing a Sand plugin's name, table prefix, route, permission, or ownership boundary. Apply `saiadmin6` for implementation details of a SaiAdmin 6.x plugin.

## Classify ownership before coding

| Capability | Owner and delivery location |
| --- | --- |
| Generic administration, installation entry, extension contract, compatibility matrix | SandAdmin host |
| Plugin domain tables, routes, menu, permissions, configuration, services, UI, lifecycle SQL | Plugin's authoritative source workspace |
| Installed `server/plugin/sand-*` or `plugins/sand-*` copy | Synchronization or acceptance material only until its authority and version are recorded |
| Identity, authorization, grants, environments, access audit | SandIAM |
| Provider/model routing, file/parse/retrieval/AI tasks, provenance and AI audit | SandAI |

Reject a host change that creates a runtime dependency on one named business plugin. Do not place a plugin's domain capability in the host merely to simplify local development.

## Repository setup and framework adoption

When establishing or taking over a SandAdmin repository:

1. Preserve upstream license, notice, and compatibility identifiers; describe the fork accurately.
2. Prove a clean zero-business-plugin PostgreSQL baseline can install, migrate, log in, and operate before claiming the host is ready.
3. Create or identify a separate plugin source workspace. Record the authority, release version, and synchronization direction for every plugin copy in the host.
4. Keep a compatibility matrix that states host version range, plugin version, dependencies, verified lifecycle environment, and known limits.

Creating a host repository does not create or own optional plugin business code. A framework consumer may use only the host; a plugin producer must use the plugin workflow below.

## Plugin delivery workflow

1. **Freeze the boundary.** Record owner, namespace/name stem, PostgreSQL table prefix, route, permission, dependency plugins, lifecycle versions, and error/DTO contract before parallel implementation.
2. **Implement at the source.** Make plugin code, UI, metadata, `install.sql`, `update.sql`, `uninstall.sql`, README, and release evidence in its authoritative workspace.
3. **Verify the package.** Run relevant syntax, type, package, and PostgreSQL-dialect checks. Treat these as static/package evidence only.
4. **Commit the plugin.** Review a scoped diff and commit the source workspace first when authorized. Do not use an untracked host mirror as the release source.
5. **Synchronize deliberately.** Copy or package the exact committed version into an independent SandAdmin validation host. Confirm deployed class/file versions, Composer/autoload mapping, and synchronization revision before testing.
6. **Run host acceptance.** In an isolated PostgreSQL environment cover zero-plugin host baseline; plugin install and load; menu/permission; one core business path; a real version upgrade; uninstall cleanup; and post-uninstall host operation. See `references/acceptance-evidence.md`.
7. **Commit host evidence separately.** Commit only host-owned compatibility, synchronization, and acceptance material after the plugin evidence is known. Never push a default branch without explicit authorization.

## SandAI and SandIAM gate

Use the SandAI-specific guardrails below before release or host claims. Read `references/sandai-iam-gate.md` when changing SandAI, SandIAM, their adapters, or their installation order.

- SandIAM owns caller identity and service authorization. SandAI consumes a defined context/authorization port; it must not query or duplicate `sand_iam_*` records.
- Missing identity context, invalid credential, grant, audience, or environment must fail closed. Never introduce an anonymous or API-key fallback as a substitute for SandIAM context.
- Do not install SandIAM, migrate its data, or reload dependent services merely because adapter/package smoke tests pass. First confirm the current SandAI plugin is synchronized into the host and has passed its own installed-host path.
- State runtime acceptance only after exercising an actual installed host with allow, deny, and audit evidence. A health response, static check, or copied directory is not sufficient.

## Evidence language and common failure modes

Label every conclusion as one of: **checked**, **modified**, **validated locally**, **committed**, **deployed**, or **verified in a real host**. Include command/output or reproducible acceptance evidence where relevant.

- A stale copied plugin or autoload map can execute older classes. Re-sync, verify the physical file/class version, then perform the reload appropriate to the host.
- A same-version empty `update.sql` is not upgrade proof. Exercise an actual source-to-target version migration.
- A successful build, SQL conversion, or package test is not an installation/login/runtime claim.
- A cross-plugin contract must be frozen before handing UI work to another contributor; include route, DTO fields, permissions, errors, and field dictionary.
- For legal or other business applications, keep final business decisions and state-changing authority in the business application. SandAI results must remain source-traceable and human-reviewable.

## Do not do

- Do not edit a source workspace and its host mirror as peers without confirming which copy is authoritative.
- Do not create plugin tables, menus, routes, permissions, configs, or services in the SandAdmin host as a shortcut.
- Do not treat package smoke checks as lifecycle acceptance, or lifecycle acceptance as authorization to publish.
- Do not invent credentials, sessions, service grants, acceptance results, or synchronization revisions.
