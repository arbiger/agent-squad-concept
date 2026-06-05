# SOP - Arbitration & Conflict Resolution

## 1. Conflict Triggers
This process starts when an Execution agent's output (e.g., Coder) is rejected by the Reviewer, or conflicts with the SP-Expert's principles.

## 2. Three-Tier Arbitration

### Tier 1: Auto-Correction Loop
- **Action**: Main synthesizes feedback from the Reviewer and SP-Expert (if active) and returns it to the Execution agent.
- **Limit**: Up to 2 cycles. If the Reviewer still rejects after cycle 2, escalate to Tier 2.

### Tier 2: Main's Direct Arbitration
- **Action**: Main analyzes the conflict between the "Execution Solution" and the "Reviewer/SP-Expert Advice."
- **Criteria**:
    - Does it violate the original goal in `Mission_Instruction.md`?
    - **SP-Expert weight**: High-weight advice. Strongly considered, but Main retains final judgment if technically justified.
    - Is the technical implementation feasible?
- **Execution**: Main makes the final call and instructs the Execution agent to proceed in a specific direction.

### Tier 3: User Escalation
- **Triggers**:
    - Main cannot determine the better option (roughly 50/50).
    - The conflict involves major design trade-offs or user value preferences.
    - SP-Expert standards fundamentally conflict with the current user command.
- **Action**: Main pauses the mission, summarizes the conflict points, and requests user arbitration.

## 3. Logging
All arbitration processes, conflict points, and final decisions must be fully recorded in `Mission_Log.md`.
