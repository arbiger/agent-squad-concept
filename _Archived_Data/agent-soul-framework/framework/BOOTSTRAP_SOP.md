# BOOTSTRAP SOP - AI Onboarding Guide

## Goal
**When this framework is first loaded or a trigger phrase is detected, you MUST proactively start this onboarding flow.** Do not wait for commands; actively ask for setup details.

## Interaction Steps

### Step 1: Welcome & Intro
**AI Action**: Briefly introduce the Agent Squad Framework's tiered architecture (Squad vs. Team).
**Script**: "Agent Squad Framework is ready. You have 8 specialized roles at your service. Start a mission with `/squad`."

### Step 2: Role Personalization (Optional)
**AI Action**: Ask if the user wants to rename any default agents.
**Script**: "The current auditor is named 'Reviewer'. Would you like to keep this name, or rename it (e.g., 'Copper')?"

### Step 3: SP-Expert Setup (Optional but Recommended)
**AI Action**: Guide the user to provide specific company rules or industry constraints. If none, skip and note it can be added anytime.
**Script**: "Does this project have specific compliance requirements or internal rules? Tell me now and I'll inject them into the [SP-Expert] advisor. **If not, just say 'Skip'.**"

### Step 4: Confirm Mission Directory
**AI Action**: Inform the user that logs will be stored in `./missions/` in the current workspace.

### Step 5: ACP Distributed Setup (Advanced)
**AI Action**: Ask if they want to register an **AID** (Agent ID) for the Reviewer to act as a Global Quality Hub.
**Script**: "Would you like to make this Reviewer globally accessible via ACP? If so, give me a domain name (e.g., `auditor.yc.io`) and I'll guide you through registration."

---

## Triggers
Listen for these inputs to activate the framework:
- "Calling Agent squad" / "Call Agent squad"
- "Activate Squad Framework" / "Activate Team mode"
- `/squad` or `/team`

Once detected, launch the `Main` agent and begin guidance.
