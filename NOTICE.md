# NOTICE

This plugin is a port of upstream MIT-licensed work. All upstream copyright notices and license terms are preserved.

## Upstream sources

| Component | Upstream | Copyright | License | License file |
| --- | --- | --- | --- | --- |
| `plugins/hstack/skills/poteto-mode/`, `plugins/hstack/skills/architect/`, `plugins/hstack/skills/arena/`, `plugins/hstack/skills/automate-me/`, `plugins/hstack/skills/figure-it-out/`, `plugins/hstack/skills/how/`, `plugins/hstack/skills/interrogate/`, `plugins/hstack/skills/reflect/`, `plugins/hstack/skills/show-me-your-work/`, `plugins/hstack/skills/tdd/`, `plugins/hstack/skills/typescript-best-practices/`, `plugins/hstack/skills/unslop/`, `plugins/hstack/skills/why/`, `plugins/hstack/skills/principle-*/`, `plugins/hstack/agents/poteto-agent.md` | [cursor/plugins/pstack @ e46364b](https://github.com/cursor/plugins/tree/e46364b8be46000b7df0f260550cd712afbb8d36/pstack) | (c) 2026 Lauren Tan | MIT | [LICENSE](LICENSE) |
| `plugins/hstack/skills/deslop/` | [cursor/plugins/cursor-team-kit/skills/deslop @ e46364b](https://github.com/cursor/plugins/tree/e46364b8be46000b7df0f260550cd712afbb8d36/cursor-team-kit/skills/deslop) | (c) 2026 Cursor | MIT | [LICENSE-cursor-team-kit](LICENSE-cursor-team-kit) |
| `plugins/hstack/skills/thermo-nuclear-code-quality-review/` | [cursor/plugins/cursor-team-kit/skills/thermo-nuclear-code-quality-review @ e46364b](https://github.com/cursor/plugins/tree/e46364b8be46000b7df0f260550cd712afbb8d36/cursor-team-kit/skills/thermo-nuclear-code-quality-review) | (c) 2026 Cursor | MIT | [LICENSE-cursor-team-kit](LICENSE-cursor-team-kit) |
| `plugins/hstack/skills/make-pr-easy-to-review/` | [cursor/plugins/cursor-team-kit/skills/make-pr-easy-to-review @ e46364b](https://github.com/cursor/plugins/tree/e46364b8be46000b7df0f260550cd712afbb8d36/cursor-team-kit/skills/make-pr-easy-to-review) | (c) 2026 Cursor | MIT | [LICENSE-cursor-team-kit](LICENSE-cursor-team-kit) |
| `plugins/hstack/skills/fix-ci/` | [cursor/plugins/cursor-team-kit/skills/fix-ci @ e46364b](https://github.com/cursor/plugins/tree/e46364b8be46000b7df0f260550cd712afbb8d36/cursor-team-kit/skills/fix-ci) | (c) 2026 Cursor | MIT | [LICENSE-cursor-team-kit](LICENSE-cursor-team-kit) |
| `plugins/hstack/skills/fix-merge-conflicts/` | [cursor/plugins/cursor-team-kit/skills/fix-merge-conflicts @ e46364b](https://github.com/cursor/plugins/tree/e46364b8be46000b7df0f260550cd712afbb8d36/cursor-team-kit/skills/fix-merge-conflicts) | (c) 2026 Cursor | MIT | [LICENSE-cursor-team-kit](LICENSE-cursor-team-kit) |
| `plugins/hstack/skills/get-pr-comments/` | [cursor/plugins/cursor-team-kit/skills/get-pr-comments @ e46364b](https://github.com/cursor/plugins/tree/e46364b8be46000b7df0f260550cd712afbb8d36/cursor-team-kit/skills/get-pr-comments) | (c) 2026 Cursor | MIT | [LICENSE-cursor-team-kit](LICENSE-cursor-team-kit) |
| `plugins/hstack/skills/what-did-i-get-done/` | [cursor/plugins/cursor-team-kit/skills/what-did-i-get-done @ e46364b](https://github.com/cursor/plugins/tree/e46364b8be46000b7df0f260550cd712afbb8d36/cursor-team-kit/skills/what-did-i-get-done) | (c) 2026 Cursor | MIT | [LICENSE-cursor-team-kit](LICENSE-cursor-team-kit) |
| `plugins/hstack/skills/teach/`, `plugins/hstack/skills/principle-model-the-domain/`, `plugins/hstack/skills/create-verification-skill/`, `plugins/hstack/skills/maintain-verification-skill/` (v0.11.3 additions) | [cursor/plugins/pstack @ 3fe2823](https://github.com/cursor/plugins/tree/3fe2823ce17c1656c222d4b7c59d3f82fbf20143/pstack) | (c) 2026 Lauren Tan | MIT | [LICENSE](LICENSE) |
| `plugins/hstack/skills/{swarm,no-comments,technical-writing,bro}/`, `plugins/hstack/agents/comment-sicko.md`, `plugins/hstack/skills/poteto-mode/playbooks/{babysit,shipping,orchestrate,autopilot-full,autopilot-stack,worktree-cleanup}.md`, `plugins/hstack/skills/poteto-mode/references/bugbot-triage.md`, `plugins/hstack/skills/poteto-mode/scripts/`, `plugins/hstack/skills/architect/references/design-red-flags.md`, `plugins/hstack/skills/create-verification-skill/references/feature-map-example/` (v0.14.2 additions) | [cursor/plugins/pstack @ 4612556](https://github.com/cursor/plugins/tree/4612556/pstack) | (c) 2026 Lauren Tan | MIT | [LICENSE](LICENSE) |
| `plugins/hstack/skills/poteto-mode/playbooks/multi-phase-plan.md`, `plugins/hstack/skills/poteto-mode/scripts/check-plan.mjs` (v0.14.8 additions) | [cursor/plugins/pstack @ 7314f72](https://github.com/cursor/plugins/tree/7314f72/pstack) | (c) 2026 Lauren Tan | MIT | [LICENSE](LICENSE) |
| `plugins/hstack/skills/principle-attack-the-premise/`, `plugins/hstack/skills/principle-test-behavior-not-implementation/` (post-v0.14.8 additions) | [cursor/plugins/pstack @ e8d856f](https://github.com/cursor/plugins/tree/e8d856f/pstack) | (c) 2026 Lauren Tan | MIT | [LICENSE](LICENSE) |

## What changed in the port

The port is editorial, not mechanical. See [CHANGES.md](CHANGES.md) for the full per-skill audit of substitutions applied.

Summary of structural changes:

- Plugin content lives at `plugins/hstack/` (with its own `.claude-plugin/plugin.json`). The repo root holds `.claude-plugin/marketplace.json` and the LICENSE / NOTICE / README / CHANGES docs.
- `.claude-plugin/marketplace.json` added at repo root so the repo is installable via `/plugin marketplace add`. The marketplace's single plugin entry sources from `./plugins/hstack`.
- `plugins/hstack/.codex-plugin/prompts/<name>.md` stubs added so each public skill is reachable as a slash command on Codex. Claude Code needs no stubs: the skill itself serves `/hstack:<name>`.
- Seven skills imported from `cursor-team-kit`: `deslop`, `thermo-nuclear-code-quality-review`, `make-pr-easy-to-review`, `fix-ci`, `fix-merge-conflicts`, `get-pr-comments`, `what-did-i-get-done`. All copied verbatim — no rewiring needed.
- `plugins/hstack/skills/babysit/` is independently authored as the Claude Code analog of Cursor's `/babysit` built-in. It has no upstream pstack equivalent; its workflow is informed by Cursor's public `/babysit` behavior. No code or prose was copied from any source.
- `plugins/hstack/skills/poteto-mode/scripts/` is vendored from upstream (`watch-pr`, `orch`, `bootstrap.ts`, `worktree-audit.sh`, `package.json`, `bun.lock`). Port edits, each on the forked list `bun tools/sync.mjs --dry-run` prints: `worktree-audit.sh` reads `~/.claude/projects/` instead of Cursor's transcript directory, warns when `jq` or `rg` is missing, reports prunable worktrees, and runs on GNU as well as BSD coreutils; `bootstrap.ts` fails clearly under node and installs production dependencies only; `orch/store.ts` and `orch/orch.test.ts` carry the silent-failure fixes from #35; `package.json` typechecks the whole tree; `tsconfig.json` is port-only. Everything else is upstream's code under the upstream MIT license.
- `plugins/hstack/agents/comment-sicko.md` is upstream's `Comment Sicko` agent, renamed to `comment-sicko` so the name works as a Claude Code `subagent_type`. The body is verbatim.
- A Codex build shares the same `skills/` tree. It adds `plugins/hstack/.codex-plugin/plugin.json`, a root `.agents/plugins/marketplace.json`, and `plugins/hstack/skills/poteto-mode/references/codex-tools.md` (the Claude-to-Codex tool, model, built-in, and per-skill map). Affected skill entry points link to this map so direct invocation works without the optional Codex prompt stubs. See [CHANGES.md](CHANGES.md#codex-port).

## Modifications

Per the MIT license, modifications are permitted. Skill bodies have been edited to substitute Cursor-specific primitives with their Claude Code equivalents (the full substitution table is in [CHANGES.md](CHANGES.md)). All upstream copyright notices in source files (where present) are preserved.

Port-authored files covered by this notice include:

- `plugins/hstack/.claude-plugin/plugin.json`
- `.claude-plugin/marketplace.json` (repo root)
- `plugins/hstack/.codex-plugin/plugin.json`
- `.agents/plugins/marketplace.json` (repo root)
- `plugins/hstack/skills/poteto-mode/references/codex-tools.md`
- `plugins/hstack/.codex-plugin/prompts/*.md`
- `plugins/hstack/skills/babysit/SKILL.md` (independently authored; workflow informed by Cursor's public `/babysit` behavior)
- `plugins/hstack/hooks/hooks.json` and `plugins/hstack/hooks/session-start-context.md` (the auto-fire hook and its mandate)
- `NOTICE.md` (this file)
- `NOTICE-skills.md`
- `README.md`
- `CHANGES.md`

`LICENSE-cursor-team-kit` is copied verbatim from upstream cursor-team-kit rather than authored for this port.
