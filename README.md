# SandAdmin Skills

Reusable Codex skills for establishing, extending, releasing, and verifying a PostgreSQL-based SandAdmin host and its optional Sand plugins.

## Included skills

### `sandadmin-host-plugins`

Use when establishing or taking over a SandAdmin repository, creating or changing a `sand-*` plugin, synchronizing a plugin into a host, preparing a release, or assessing SandAI/SandIAM lifecycle acceptance.

It enforces a clear separation between the zero-plugin SandAdmin host, an authoritative plugin source workspace, host synchronization, and real lifecycle evidence.

## Install

Install the skill from this repository with Codex's skill installer:

```bash
python3 /path/to/install-skill-from-github.py \
  --repo supdger/sandadmin-skills \
  --path skills/sandadmin-host-plugins
```

Or copy `skills/sandadmin-host-plugins` into `~/.codex/skills/`.

## Use

Invoke it explicitly with:

```text
Use $sandadmin-host-plugins to classify this SandAdmin change and prepare its delivery path.
```

The skill can also match work involving SandAdmin repository setup, Sand plugin delivery, host synchronization, and SandAI/SandIAM integration.

## License

MIT. See [LICENSE](LICENSE).
