# `_Archived_Data/` — Lineage & Findings

> **Archive of historical implementations** of the multi-agent squad idea,
> preserved as part of `agent-squad-concept` (the public concept record).
> The current canonical skill lives in `../SKILL.md` and the opencode
> runtime config at `~/.config/opencode/`.

## Contents

### Three cloned private repos (snapshotted 2026-06-05, shallow clone at HEAD)

| Folder | Source | Files | Description |
|---|---|---:|---|
| `agent-soul-framework/` | `arbiger/agent-soul-framework` (private) | 95 | AI Agent Design Pattern: SOUL + HEARTBEAT + IDENTITY for personality-driven AI assistants |
| `calling-agent-squad/` | `arbiger/calling-agent-squad` (private) | 29 | OpenClaw Agent Squad Framework — Anthropic handover-driven workflow |
| `openclaw-calling-agent-squad/` | `arbiger/openclaw-calling-agent-squad` (private) | 63 | Original OpenClaw multi-agent squad skill |

All three were private on GitHub at snapshot time. Their contents are mirrored here as public archive snapshots for context. Inner `.git/` directories were stripped to avoid submodule complexity in this parent repo.

### Other archived material (predates 2026-06-05)

| Item | Notes |
|---|---|
| `agent-soul-framework.local-2025-04/` | Earlier local copy of the agent-soul-framework files (April 2025). Preserved alongside the GitHub version for diff. |
| `_Archived_Agent-Scripts/` | Older agent-scripting experiment from April 2025 (AGENTS.md, SOUL.md, HEARTBEAT.md, etc.) |
| `README.md.concept` / `SKILL.md.concept` / `SPEC.md.concept` | Earlier concept drafts of the agent-squad docs |
| `docs/superpowers/plans/` & `specs/` | Earlier planning + design docs |
| `roles/architect.md`, `blue-reviewer.md`, `coder.md`, `red-reviewer.md` | Earlier role definitions (predecessor to current opencode agent-squad) |
| `log.md.template` | Earlier log template |

---

## Progress — Session of 2026-06-05

The live `agent-squad` architecture (in `~/.config/opencode/`) was restructured:

1. **Two-Stage Review added** — PM-Reviewer (hard gate) + ccl-red-team/fpr-reviewer (optional, substantial work). Mirrors the "audit subagent" lesson from charge/amplify.
2. **Planner/PM-Reviewer split** — Planner now *creates* plans; PM-Reviewer *reviews* them, invoked twice per workflow (pre-impl + post-impl).
3. **qwen-worker removed** — experimental, never wired into main flow.
4. **`opencode.json` restructured** — 6 custom agents in flow order (team-lead → planner → pm-reviewer → fpr-reviewer → codex-executor → coder).
5. **`SKILL.md` updated** — see `../SKILL.md` for current canonical.

---

## Findings — 4-repo comparison

### Timeline / lineage

```
2026-03-18  openclaw-calling-agent-squad    ← original OpenClaw skill
2026-03-23  calling-agent-squad              ← refactored: 8-agent framework (9.4MB)
2026-04-01  agent-soul-framework             ← META: SOUL/HEARTBEAT/IDENTITY pattern
2026-04-25  (agent-soul-framework integrates the two calling-* repos + Claude Code template)
2026-05-02  agent-squad-concept              ← renamed/sunset as concept record
2026-06-05  agent-squad-concept (this commit)← mirrors opencode-config live skill
```

### Role mapping: old 8-agent framework → current 5-agent opencode architecture

| Old role (`calling-agent-squad`) | Current opencode equivalent |
|---|---|
| **Main** (決策者 — project director) | `team-lead` |
| **Parser** (分析者 — decomposes user intent) | `planner` |
| **Reviewer** (審閱者 — red team QA) | `pm-reviewer` (invoked **twice**: pre-impl + post-impl) |
| **Coder** (開發者 — code + debug) | `coder` |
| **Researcher / Analyst / Writer** | _No direct equivalent — folded into `planner` + `pm-reviewer` scope_ |
| **SP-Expert** (選配 — injects company/industry context) | `fpr-reviewer` (optional) + `codex-executor` (special tasks) |

### Key observations

1. **8-agent → 5-agent is a deliberate simplification.** Fewer roles with explicit hand-offs beat more specialized roles. Matches the "dynamic generation is a pseudo-need" lesson from the article on `charge`/`amplify` — static named roles win.
2. **`agent-soul-framework` is the meta-framework.** Its April 25 commit explicitly integrates the two `calling-*` repos and adds a "Claude Code template" — it's the most architecturally rich of the four.
3. **`agent-squad-concept` is the concept record.** Implementation now lives in `~/.config/opencode/` (opencode runtime), not in this GitHub repo.
4. **No clear "owner" of the live code from this archive's perspective.** The concept record points to opencode runtime, not to the 3 archived repos. The archived repos are pure historical record.
5. **The "SOUL/HEARTBEAT/IDENTITY" pattern is orthogonal to the squad pattern.** `agent-soul-framework` is about *how an individual agent has personality*; the squad pattern is about *how multiple agents coordinate*. They compose, but solve different problems.

---

## Related live locations (for navigation)

- **Current canonical skill**: `../SKILL.md` (and `~/.config/opencode/skills/agent-squad/SKILL.md`)
- **Live opencode agent definitions**: `~/.config/opencode/opencode.json`
- **Source repos** (private, on GitHub):
  - https://github.com/arbiger/agent-soul-framework
  - https://github.com/arbiger/calling-agent-squad
  - https://github.com/arbiger/openclaw-calling-agent-squad
