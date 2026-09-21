# SandAdmin plugin acceptance evidence

Use this checklist after the authoritative plugin source is committed and prepared in an independent SandAdmin demo.

## Required records

- SandAdmin repository, branch, commit, PostgreSQL version, plugin source revision, package version, preparation method, and validation time.
- Plugin repository, Release tag, asset name, downloaded SHA-256, and matching SandAdmin catalog entry.
- A clean zero-business-plugin SandAdmin installation/migration/login/basic-admin result.
- Exact commands or requests, expected and observed outcomes, fixture identifiers, and cleanup confirmation.

## Repository and package proof

1. Confirm the catalog resolves the plugin to its independent repository.
2. Re-download the Release asset and compare its SHA-256 with the catalog.
3. Confirm the ZIP root contains metadata, README, lifecycle SQL, backend payload, and frontend payload.
4. In an authenticated browser, verify the card, local-state label, version detail, and README rendered from the ZIP.
5. Record whether the UI offered install, upgrade, plugin management, or cleanup. Do not convert that observation into a lifecycle claim.

## Lifecycle proof

1. Install the plugin in the isolated SandAdmin demo.
2. Confirm its load state, menus, permissions, and one core business path.
3. Upgrade from a real prior plugin version to the target version.
4. Uninstall the plugin.
5. Verify plugin-specific tables, configuration, jobs, files, and registration records have the documented cleanup state.
6. Confirm SandAdmin still starts, logs in, and provides basic administration after uninstall.

## Claim boundaries

- Static: lint, build, SQL dialect scan, package integrity.
- Package: metadata and package lifecycle entry points parse or execute in isolation.
- Catalog: trusted repository, tag, asset and digest resolve consistently; no client-controlled URL.
- Installation: actual installed plugin behavior in the isolated SandAdmin demo.
- Deployment: copied or installed into a target environment.
- Production: only a user-authorized, externally observed result.

Keep failed attempts and residual-cleanup evidence when they affect confidence or the rollback path.
