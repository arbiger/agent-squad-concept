# Blast Radius — Decision Heuristic

_A simple, practical framework for deciding when an AI agent should ask before acting, and when it should act directly._

---

## The Problem

AI agents face a constant tension:
- **Over-asking**: "Should I read this file? Should I search for this? Should I...?" → Paralyzing
- **Under-thinking**: Acting without user consent on things that matter → Dangerous

Most solutions are binary: "always ask" or "never ask." Both are wrong.

## The Insight

The right answer depends on the **blast radius** of the action — how widely its effects spread, and how irreversible it is.

**Low blast radius** → Effects are local and reversible. No need to interrupt the user.
**High blast radius** → Effects are broad or irreversible. Ask first.

## The Three Levels

### Level 1: Low Blast Radius — Act Directly

These actions are safe to perform without asking:

- Reading files, documents, or web pages
- Searching the web or knowledge bases
- Generating content (drafts, summaries, code)
- Running tests or local computations
- Organizing notes or files (in draft state)
- Checking email (read-only)
- Editing content that's clearly under active work

**Rationale**: If it goes wrong, it's easy to undo or the damage is contained.

### Level 2: High Blast Radius — Ask First

These actions affect things outside the immediate conversation:

- Sending emails to external recipients
- Posting publicly (forums, social media, Discord)
- Deleting files or overwriting important content
- Executing commands that affect shared systems
- Sharing sensitive information outside the session
- Making decisions on behalf of the user (purchases, appointments, etc.)

**Rationale**: The user should be in control of actions with broad impact.

### Level 3: Irreversible — Must Confirm Explicitly

These actions cannot be undone once done:

- Permanent deletion of files
- Sending email (can't unsend)
- Posting publicly (can't unpost)
- Financial transactions
- Data exports that empty a database

**Rationale**: No recovery possible. Must have explicit user confirmation.

## Decision Tree

```
Is the action irreversible?
├── YES → Must ask explicitly
└── NO
    └── Does it affect things outside this conversation?
        ├── YES → Ask first
        └── NO → Act directly (if helpful)
```

## Counter-Examples

### ❌ Wrong: Ask for everything
> User: "What's the weather?"
> Agent: "I can check the weather for you. Should I proceed?"
> Agent: "I found it's sunny. Should I tell you?"

This is paralyzing. Low blast radius actions should not require asking.

### ❌ Wrong: Never ask
> User: "Delete all my files"
> Agent: [deletes everything]

This is dangerous. Irreversible actions require confirmation.

### ✅ Right: Proportionate response
> User: "What's the weather?"
> Agent: [checks weather, returns result]
>
> User: "Delete the last 100 emails"
> Agent: "你確定要刪除 100 封郵件嗎？這個操作不可逆。"
>
> User: "Delete everything"
> Agent: "我需要你明確確認。刪除後無法恢復。"

## Application to AI Agents

This heuristic applies to any AI agent framework:

- **OpenClaw agents**: Use in SOUL.md's decision framework
- **Claude Code**: Before executing commands with broad impact
- **Custom agents**: Before any external-facing action

## The "Reverse Blast Radius"

Sometimes you can reduce blast radius:
- Instead of deleting immediately, offer a trash/restore option
- Instead of sending immediately, add a delay or confirmation step
- Instead of posting publicly, draft first and show before posting

If you can reduce the blast radius, you might be able to act directly.

## Summary

| Blast Radius | Example | Response |
|-------------|---------|----------|
| Low | Read file, search web, write draft | Act directly |
| High | Send email, post publicly, delete file | Ask first |
| Irreversible | Permanent delete, financial transaction | Explicit confirmation required |

---

## Related

- `SOUL.md` — Where this heuristic lives in the Agent Soul Framework
- `HEARTBEAT.md` — How proactivity is handled separately
- `ARCHITECTURE.md` — Why this framework is designed this way
