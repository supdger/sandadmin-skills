# SandAdmin Skills

Reusable Codex skills for setting up SandAdmin, releasing independent Sand plugins, and verifying real installations.

## Included skills

### `sandadmin-plugins`

Use when setting up SandAdmin, publishing a `sand-*` plugin from its independent repository, updating the plugin catalog, preparing a demo installation, or verifying install, upgrade, cleanup, and uninstall behavior.

It separates the clean SandAdmin framework, each plugin's source repository, catalog metadata, demo copies, and real installation evidence.

## Install

Install the skill from this repository with Codex's skill installer:

```bash
python3 /path/to/install-skill-from-github.py \
  --repo supdger/sandadmin-skills \
  --path skills/sandadmin-plugins
```

Or copy `skills/sandadmin-plugins` into `~/.codex/skills/`.

When upgrading from the former name, install `sandadmin-plugins` and move
`~/.codex/skills/sandadmin-host-plugins` outside the Skills directory. Keeping
both directories makes Codex discover two versions of the same workflow.

## Use

Invoke it explicitly with:

```text
Use $sandadmin-plugins to classify this SandAdmin or plugin release change and prepare its delivery path.
```

The skill can also match work involving SandAdmin repository setup, plugin delivery, demo synchronization, and SandAI/SandIAM integration.

## License

MIT. See [LICENSE](LICENSE).
