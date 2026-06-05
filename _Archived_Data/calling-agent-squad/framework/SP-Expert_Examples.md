# SP-Expert Usage Examples

Generic examples showing how to use SP-Expert for quality and compliance control across different industries.

---

## Example 1: Branding & Terminology
**Setup**:
- "We are a partner-centric company. Strictly avoid the word 'Customer' in all outputs. Use 'Partner' instead."
- "All 'Bugs' in external reports must be referred to as 'Optimization Items'."

## Example 2: Security & Privacy
**Setup**:
- "Hard-coded API Keys or passwords are strictly prohibited — even in testing. Use environment variables always."
- "All user data fields (e.g., Email) must be masked or de-identified in mission logs."

## Example 3: Architecture & Performance
**Setup**:
- "Lightweight deployment only. Third-party libraries must be under 500KB unless explicitly authorized by Main."
- "Database queries must use indexes. Full table scans are prohibited."

## Example 4: Legal & Compliance Strategy
**Setup**:
- "For products in Region X, avoid specific color combinations to respect local customs."
- "All promotional copy must include the disclaimer 'Actual results may vary'."

---

### Usage Suggestion
Fill your `EXPERT_KNOWLEDGE.md` with rules like these. `Main` loads them at startup and `SP-Expert` monitors compliance throughout the mission.
