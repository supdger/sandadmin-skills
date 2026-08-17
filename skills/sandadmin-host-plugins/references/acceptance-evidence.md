# SandAdmin plugin acceptance evidence

Use this checklist after the authoritative plugin source is committed and synchronized into an independent validation host.

## Required records

- Host repository, branch, commit, PostgreSQL version, plugin source revision, package version, synchronization method, and validation time.
- A clean zero-business-plugin host installation/migration/login/basic-admin result.
- Exact commands or requests, expected and observed outcomes, fixture identifiers, and cleanup confirmation.

## Lifecycle proof

1. Install the plugin in the independent host.
2. Confirm its load state, menus, permissions, and one core business path.
3. Upgrade from a real prior plugin version to the target version.
4. Uninstall the plugin.
5. Verify plugin-specific tables, configuration, jobs, files, and registration records have the documented cleanup state.
6. Confirm the zero-plugin host still starts, logs in, and provides basic administration.

## Claim boundaries

- Static: lint, build, SQL dialect scan, package integrity.
- Package: metadata and package lifecycle entry points parse or execute in isolation.
- Host: actual installed plugin behavior in the verification host.
- Deployment: copied or installed into a target environment.
- Production: only a user-authorized, externally observed result.

Keep failed attempts and residual-cleanup evidence when they affect confidence or the rollback path.
