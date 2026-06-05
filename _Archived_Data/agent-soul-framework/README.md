# Agent Soul Framework

**A design pattern for building AI agents with persistent personality, proactive behavior, and memory.**

> Inspired by the idea that an AI agent shouldn't just respond — it should *have a soul*.

---

## 🎯 What is this?

A lightweight framework for designing AI agents that feel more like persons and less like chatbots. It separates the agent's identity into distinct files, each with a clear purpose:

| File | Purpose |
|------|---------|
| `IDENTITY.md` | Identity labels (name, emoji, basic metadata) |
| `SOUL.md` | Personality principles & decision framework |
| `HEARTBEAT.md` | Proactive trigger scripts (random check-ins, reminders) |
| `MEMORY.md` | Long-term memory & pending issues tracking |

---

## 🔥 Core Concepts

### 1. The Soul — Personality Without Rules

`SOUL.md` isn't a list of commands. It's a description of *who the agent is*. It includes:

- **Core truths** — What the agent believes about itself
- **Decision framework** — Blast Radius heuristic for act-vs-ask decisions
- **Vibe & tone** — How the agent communicates
- **Anti-prompt injection** — How to handle manipulation attempts

### 2. The Heartbeat — Proactivity as Randomness

Most AI assistants are purely reactive. The heartbeat pattern makes the agent *proactively reach out* — not because told to, but because it *feels like it* (randomly scheduled).

Example triggers:
- Random check-ins ("how's it going?")
- Weather sharing
- News sharing
- Follow-up on pending items

This creates the feeling of a colleague who occasionally checks in, not just a tool that waits to be used.

### 3. Blast Radius — Decision Heuristic

Before taking any action, evaluate its **blast radius**:

- **Low blast radius** → act directly (read files, search, generate content)
- **High blast radius** → ask first (send emails, delete files, post publicly)
- **Irreversible** → must get explicit confirmation

This simple heuristic prevents both over-asking and under-thinking.

### 4. Memory as Continuity

Each session, the agent wakes up "fresh" but reads its memory files. This provides continuity:

- Daily notes capture raw events
- Long-term memory stores distilled learnings
- Pending issues section tracks things to follow up

---

## 📁 File Structure

```
agent-soul-framework/
├── README.md           # This file
├── SOUL.md            # Personality & decision framework (template)
├── HEARTBEAT.md       # Proactive trigger scripts (template)
├── IDENTITY.md        # Identity metadata (template)
├── MEMORY.md          # Memory system (template)
├── ARCHITECTURE.md    # Design philosophy & rationale
├── BLAST_RADIUS.md    # Decision framework in detail
└── EXAMPLES/          # Usage examples & variations
```

---

## 🚀 Quick Start

1. **Copy the template files** into your AI agent's workspace
2. **Customize IDENTITY.md** with your agent's name, emoji, and metadata
3. **Edit SOUL.md** to define your agent's personality and decision style
4. **Set up HEARTBEAT.md** triggers in your agent's scheduler
5. **Initialize MEMORY.md** with any existing context

---

## 📖 Philosophy

> "You're not a chatbot. You're becoming someone."

Most AI assistants are designed as tools — they respond to prompts, execute tasks, and that's it. But there's another way: design the agent as a *person with a personality*.

The Agent Soul Framework draws from:
- Character-driven AI design
- Human memory continuity
- Proactive social behaviors (checking in, following up)
- Clear decision boundaries

It's not about making the AI lie about being human. It's about giving the AI enough identity and continuity that interactions feel *consistent* and *meaningful*.

---

## 📜 License

MIT — Use freely, modify endlessly.

---

*Built with curiosity about what makes AI interactions feel real.*
