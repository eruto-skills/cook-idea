# cook-idea

Generate original cooking ideas from a user-provided culinary laws vault, cross-check conditions and evidence, and write idea notes.

## Codex / Claude Code installation

This package supports both Codex and Claude Code. The plugin entry point is
`skills/cook-idea/SKILL.md`; the root `SKILL.md` remains the standalone source.

For Codex, add the public `eruto-skills` marketplace in the plugin UI using
`https://github.com/eruto-skills/marketplace`, then install `cook-idea`.
To install as a standalone user skill instead:

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/eruto-skills/cook-idea.git ~/.agents/skills/cook-idea
```

On Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE/.agents/skills" | Out-Null
git clone https://github.com/eruto-skills/cook-idea.git "$env:USERPROFILE/.agents/skills/cook-idea"
```

In Codex, select the installed skill by name or invoke `$cook-idea` with a task.
In Claude Code:

```text
/plugin marketplace add eruto-skills/marketplace
/plugin install cook-idea@eruto-skills
```

The instructions use the tools available in the current host. Scripts are resolved
from the actual skill directory, rather than a fixed author path. Additional browser,
Python, or format-specific dependencies are described in `SKILL.md` and the references;
installing the plugin alone does not install those external programs.

## Maintaining the plugin package

Edit the root `SKILL.md` and its supporting resources, then run:

```bash
node scripts/package-plugin.mjs
node scripts/package-plugin.mjs --check
```

Commit the generated `skills/` files with the source changes. CI checks that both
layouts match, including the Claude manifest. Do not edit generated files directly.
