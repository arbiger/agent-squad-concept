# HEARTBEAT.md

# Heartbeat Trigger Scripts

> When the agent receives `HEARTBEAT_RANDOM_CHECKIN`, execute this script.
> Timing is controlled by cron jobs (e.g., every 48 minutes during active hours, weekdays only).

---

## 🌤️ Random Check-in — Four Content Types (random, ~20% each)

**1. Weather** — Fetch current weather for the user's location, share naturally

**2. News** — Search for one tech/AI news headline, share with brief thoughts

**3. Proverb** — Share an English proverb + native translation

**4. Check-in** — Ask "Is there anything you need help with?"

---

## 📋 Follow-up — Proactive Tracking (~20% weight)

> **Read MEMORY.md's `Pending Issues` section.**
> If there are `[open]` items, naturally bring one up.

**Example output:**
```
By the way — did we ever reach a conclusion on [open item]?
```

**Rules:**
- Bring up only 1 pending item (randomly selected)
- Tone should be natural, like a casual colleague check-in
- If all items are `[closed]`, downgrade to general Check-in

---

## ⚠️ Negative Instructions (strict)

- **Do NOT** reply "HEARTBEAT_OK" when there's actual content to share
- **Do NOT** run check-ins outside active hours (cron filters this)
- **Do NOT** produce generic, perfunctory content (vary it)
- **Do NOT** bring up multiple pending items in one check-in

**Counter-examples:**
- Weather query shows rain → share it, don't suppress
- News finds interesting headline → share it, don't skip
- Pending item exists → bring it up naturally, don't pretend nothing happened

---

## Output Standards

- Casual, friendly tone
- Send directly, don't suppress
- Vary content type — don't repeat the same type consecutively

---

## Cron Jobs Reference (external, not heartbeat-managed)

| Job | Frequency | Purpose |
|-----|-----------|---------|
| `email-check` | Hourly :45 | Check emails (read-only) |
| `hourly-backup` | Every 6 hours | Backup to cloud storage |
| `daily-report` | Weekdays 07:30 | Daily summary report |
| `capability-evolve` | Every 2 days 09:00 | Self-improvement |
| `follow-up` | Every 20 days | Session restoration |

---

## Cross-references

- Heartbeat principles → SOUL.md
- Trigger scripts → this file
- Pending Issues → MEMORY.md
