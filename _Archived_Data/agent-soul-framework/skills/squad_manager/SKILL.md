# SKILL - Squad Manager

## Description
Core driving logic for the `Main` agent. Dynamically selects between "Squad (Session)", "Team (Sub-agent)", or "Distributed (ACP)" modes based on task complexity, duration, and isolation needs.

## 🔹 Onboarding Instruction
When activated or "Call Agent squad" is detected, **refer to `framework/BOOTSTRAP_SOP.md`**. Actively ask the user about:
1. Agent renaming preferences.
2. SP-Expert rules to inject.
3. Mission report storage location.

## Decision Matrix

| Dimension | Squad (`sessions_spawn`) | Team (`/subagents spawn`) | Distributed (ACP) |
| --- | --- | --- | --- |
| **Complexity** | Low–Medium (single task) | Medium–High (multi-step) | Extreme (distributed/external) |
| **Duration** | Short (< 5 min) | Long (> 5 min, background) | Long-term, needs external agents |
| **Reporting** | Sync wait or active query | Async status updates | Real-time via ACP channel |
| **Typical Task** | Syntax check, quick search | New features, deep research | Cross-platform, ACP-networked agents |

## Triggers
- **Slash Commands**: `/squad`, `/team`, `/acp`
- **Natural Language**:
    - "Call Agent squad" / "Calling Agent squad"
    - "Activate Team mode"
    - "Start mission"

## Tool Commands

### 1. `delegate_task`
**Params**: `task_description`, `preferred_agent`, `mode` (auto|squad|team|acp)
**Action**:
- `squad`: Spawn role session and wait for result (with short timeout).
- `team`: Spawn background Sub-agent and record `runId`.
- `acp`: Use `acp send` to communicate with a specific **AID** (Agent ID).
- `auto`: Main decides based on task description.

### 2. `monitor_team`
**Params**: `run_id` (optional)
**Action**:
- Use `subagents list` for all background statuses.
- Use `subagents log` for real-time progress of a specific `run_id`.

### 3. `collect_results`
**Action**:
- Upon completion, trigger `Reviewer` for audit.
- Send audited output to `Main` for final integration.

## Notes
- `Main` must always report: "Delegating [Task] to [Agent] via [Squad/Team/ACP] mode."
