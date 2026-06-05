# SKILL - Mission Logger

## Description
Manages all mission files under `./missions/`. Ensures every mission has structured instructions, logs, and output records.

## Tool Commands

### 1. `init_mission`
**Params**: `mission_name`, `instructions`
**Action**:
- Create `./missions/[mission_name]-report/` directory.
- Create `outputs/` sub-directory.
- Write `Mission_Instruction.md` with goals and task breakdown.

### 2. `log_activity`
**Params**: `mission_name`, `agent_role`, `content`, `reviewer_feedback` (optional)
**Action**:
- Append to `Mission_Log.md`.
- Format:
  ```markdown
  ## [Timestamp] - [Agent Role] Output
  Content: ...
  Reviewer Feedback: ...
  ```

### 3. `save_output`
**Params**: `mission_name`, `filename`, `content`
**Action**:
- Write `content` to `./missions/[mission_name]-report/outputs/[filename]`.

## Usage Example
`Main` calls `init_mission` at start, then `log_activity` and `save_output` after each agent completes their work.
