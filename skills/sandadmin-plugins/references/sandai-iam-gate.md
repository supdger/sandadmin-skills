# SandAI and SandIAM integration gate

Use this reference when changing the SandAI plugin, SandIAM plugin, an identity-context adapter, or an installation order.

## Ownership

- SandIAM: organization, identity, application, environment, workload client, credential, service grant, policy, data scope, and access audit.
- SandAI: provider/model/capability routing, files, parsing, retrieval, AI tasks, usage, provenance, and AI-result audit.
- Business application: its own records, visibility rules, final state transitions, and human approvals.

## Mandatory boundaries

- Consume authorization through the documented adapter/port; do not issue cross-database reads of `sand_iam_*` from SandAI.
- Validate credential, client, environment, grant, audience, and action in the identity context. Missing or invalid context fails closed.
- Keep secret material write-only and never claim a copied package is a running, synchronized installation.

## Ordered acceptance

1. Confirm the authoritative SandAI package and the exact revision prepared in SandAdmin.
2. Complete the SandAI installed path and prove the prepared package remains unchanged.
3. Only then install or migrate SandIAM and test the adapter.
4. Exercise a real SandAI business API with permitted, denied, and audited outcomes.
5. Confirm test fixtures, temporary credentials, and audit fixtures have the documented cleanup state.

Do not infer this final step from health checks, package smoke tests, or SandIAM-only installation acceptance.
