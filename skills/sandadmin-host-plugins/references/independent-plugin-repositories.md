# Independent Sand plugin repositories

Use this reference for repository splits, Release publication, SandAdmin catalog changes, and retirement of an aggregate plugin repository.

## Ownership model

- `supdger/sandadmin` owns the zero-business-plugin host, `plugins/catalog.json`, trusted download rules, package validation, plugin management, and lifecycle entry points.
- Each `sand-*` repository owns one plugin's complete source, root metadata, lifecycle SQL, backend and frontend payloads, documentation, tests, tags, and Release assets.
- Installed directories and validation-host copies are consumers. They are never parallel authoritative sources.
- An old aggregate repository is migration evidence only after each plugin has an independent authoritative repository.

## Split and publication checks

For every plugin:

1. Split from a committed clean source revision so directory history is retained.
2. Add a migration record containing the aggregate source revision, split revision, and new authority.
3. Confirm the independent repository contains `README.md`, `info.ini`, `config.json`, `install.sql`, `update.sql`, `uninstall.sql`, the backend payload, and the frontend payload.
4. Commit repository-specific ownership wording and remove absolute paths or aggregate-workspace defaults from scripts.
5. Build the ZIP from a committed revision, publish it in that plugin repository, download it again, and record the SHA-256.
6. Update SandAdmin's catalog only after the asset exists. The entry must use a constrained `owner/repository`, immutable tag, exact asset name, compatible host range, and downloaded digest.
7. Run catalog contract tests and authenticated browser checks before removing an older referenced Release.

## Catalog and installer boundary

The catalog repository may be mutable, but every selected plugin package is fixed by repository, tag, asset, version, and digest. Acceptance must record and verify the catalog revision that the host actually loaded; a branch name or successful push alone does not prove the running host consumed that revision.

The frontend may choose an app and advertised version. It must not send or override a repository URL. The server fetches the catalog, validates repository syntax, derives the GitHub Release URL, downloads the asset, verifies the digest, validates the package identity and version, then stages it for the existing installer.

Downloading or reading the README must not execute SQL, deploy runtime files, or create an installed registration.

## Retiring an aggregate repository

Before archiving or deleting an aggregate repository:

1. Confirm SandAdmin's current catalog references only independent repositories.
2. Confirm every independent repository contains the intended source history and currently published asset.
3. Inventory local clones for modified and untracked work. Migrate useful source, migrations, tests, host requests, and acceptance evidence before deleting the remote baseline.
4. Remove duplicate aggregate Releases only after their replacements are re-downloaded and their catalog digests match.
5. Prefer archiving while unresolved local work or external consumers may still need the old history. Delete only with explicit authorization after those dependencies are resolved.

Archiving or deleting a remote repository does not preserve uncommitted local work.
