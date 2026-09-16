# hstack

A personal Claude Code plugin: agent workflows for understanding a codebase,
designing changes, testing fixes, and preparing pull requests. It's a
pared-down fork of Lauren Tan's `pstack`, kept to a single Claude Code target
with the generator/sync tooling and the parallel Codex build stripped out.

Start with `poteto-mode` to pick a workflow, or invoke a specific skill
directly when you know what you need.

## Install

```shell
/plugin marketplace add HavardPede/hstack
/plugin install hstack@hstack
```

The plugin's `SessionStart` hook (`plugins/pstack/hooks/`) loads a short
instruction on startup, `/clear`, and after compaction, directing non-trivial
tasks to `poteto-mode`. To disable it, delete `hooks/hooks.json` from the
installed plugin; an update restores the file.

## Use it

```text
Use poteto-mode to add pagination to the search results.
Use how to explain the request path from the API handler to the database.
Use tdd to reproduce this failing case, then fix it.
Use interrogate to review my diff for bugs and missing cases.
```

Each skill is also a slash command: `/pstack:poteto-mode`, `/pstack:how`, and
so on.

## Skill catalog

31 workflow skills, grouped by purpose. A further 23 `principle-*` skills hold
the guidance `poteto-mode` reads when it names a principle behind a decision;
they aren't meant to be invoked directly.

| Group | Skills |
| --- | --- |
| Understand | `how`, `why`, `teach`, `recall`, `bro`, `blast-radius` |
| Design & build | `architect`, `arena`, `swarm`, `figure-it-out` |
| Test & review | `tdd`, `interrogate`, `thermo-nuclear-code-quality-review`, `no-comments`, `deslop`, `unslop`, `typescript-best-practices` |
| Ship & PR ops | `babysit`, `fix-ci`, `fix-merge-conflicts`, `get-pr-comments`, `make-pr-easy-to-review`, `what-did-i-get-done` |
| Meta / setup | `poteto-mode`, `automate-me`, `reflect`, `setup-pstack`, `create-verification-skill`, `maintain-verification-skill`, `technical-writing`, `show-me-your-work` |

## How routing works

`poteto-mode` is the entry point. It reads the task, applies the relevant
`principle-*` guidance, and for task shapes with a matching pattern (feature,
bug fix, shipping a PR, babysitting CI, a large migration) hands off to a
playbook under `plugins/pstack/skills/poteto-mode/playbooks/`. Narrower
requests skip the playbook and go straight to a specific skill instead, such
as `architect` for a design pass or `interrogate` for an adversarial review.

## Configure models

Run `setup-pstack` to choose Claude models per role. Defaults live in
[models.json](plugins/pstack/models.json); the override sheet is
`~/.claude/pstack-models.md`.

## Repository layout

```text
.claude-plugin/marketplace.json    Claude Code marketplace
plugins/pstack/
  .claude-plugin/plugin.json       Claude Code plugin manifest
  skills/                          Skills, references, and scripts
  agents/                          Claude Code subagent definitions
  hooks/                           SessionStart routing hook
  models.json                      Per-role model defaults
tests/                             Repository checks (Bun)
```

## Origin

This plugin is a fork. Skill content is derived from:

- [pstack](https://github.com/cursor/plugins/tree/main/pstack) by Lauren Tan
  (MIT).
- Seven skills from [cursor-team-kit](https://github.com/cursor/plugins/tree/main/cursor-team-kit)
  by Cursor (MIT): `deslop`, `thermo-nuclear-code-quality-review`,
  `make-pr-easy-to-review`, `fix-ci`, `fix-merge-conflicts`,
  `get-pr-comments`, `what-did-i-get-done`.

Both licenses are preserved in full: [LICENSE](LICENSE) (pstack) and
[LICENSE-cursor-team-kit](LICENSE-cursor-team-kit) (cursor-team-kit).
[NOTICE.md](NOTICE.md) records which upstream revision each file traces back
to and what was modified in this fork.
