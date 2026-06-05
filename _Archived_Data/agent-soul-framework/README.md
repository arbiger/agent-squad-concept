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

## 📁 Directory Structure

```
agent-soul-framework/
├── README.md                 # This file
├── SOUL.md                   # Personality & decision framework
├── IDENTITY.md               # Identity metadata
├── HEARTBEAT.md              # Proactive trigger scripts
├── MEMORY.md                 # Long-term memory
├── ARCHITECTURE.md           # Design philosophy & rationale
├── BLAST_RADIUS.md           # Decision framework in detail

├── framework/                # Multi-agent squad framework (from calling-agent-squad)
│   ├── Main.md              # Leader/Manager agent - coordinates team
│   ├── Parser.md            # Task decomposer
│   ├── Reviewer.md           # Red-team QA - "I can oppose, but I must make you better"
│   ├── Execution_Roles.md    # Coder, Analyst, Writer, Researcher, etc.
│   ├── Support_Roles.md      # SP-Expert, Observer, etc.
│   ├── Arbitration_Workflow.md
│   ├── BOOTSTRAP_SOP.md
│   └── Customization_Guide.md

├── agents/                   # Pre-defined agent configs (from openclaw-calling-agent-squad)
│   ├── squad-manager/       # SOUL, IDENTITY, HEARTBEAT, TOOLS, USER, AGENTS
│   ├── architect/
│   ├── researcher/
│   ├── coder/
│   ├── code-reviewer/
│   ├── brand-reviewer/
│   ├── copywriter/
│   └── observer/

├── skills/                   # OpenClaw skills
│   ├── mission_logger/
│   ├── open-claude-design/
│   ├── squad_manager/
│   └── taskpad/

├── claude-code/              # Claude Code specific
│   └── CLAUDE_CODE_LEAKS.md  # Prompt template with 6 key areas

├── templates/
│   └── handbook.md

├── squad-init.sh            # Squad initialization script
└── squad-manager.prose       # Squad manager documentation
```

---

## 👥 Multi-Agent Squad Pattern

The framework supports a **leader + sub-agents** pattern:

1. **Squad Manager (Main)** — Coordinates the team, delegates tasks, runs arbitration
2. **Architect** — System planning and blueprint design
3. **Researcher** — Information gathering and fact-checking
4. **Coder** — Code implementation
5. **Reviewer** — Red-team QA: *"I can oppose, but I must make you better"*
6. **Copywriter** — Marketing and technical content
7. **Observer** — Mission logging and tracking

### Red-Team Reviewer (Key Concept)

The Reviewer agent is not a "yes-man." Its role:
- Active opposition to improve quality
- Fatal issues must be reported immediately
- General advice for optimization
- Slogan: *"I can oppose, but I must make you better"*

---

## 🚀 Quick Start

### Single Agent
1. Copy `SOUL.md`, `IDENTITY.md`, `HEARTBEAT.md`, `MEMORY.md` to your agent's workspace
2. Customize with your agent's personality
3. Set up heartbeat triggers

### Multi-Agent Squad
1. Use `squad-init.sh` to initialize a project
2. Configure roles in `framework/` directory
3. Each agent has its own SOUL/IDENTITY/HEARTBEAT in `agents/`
4. Leader agent runs arbitration through Reviewer

### Claude Code
See `claude-code/CLAUDE_CODE_LEAKS.md` for prompt template with:
- Plan Mode Default
- Subagent Strategy
- Self-Improvement Loop
- Verification Before Done
- Demand Elegance
- Autonomous Bug Fixing

---

## 📖 Philosophy

> "You're not a chatbot. You're becoming someone."

Most AI assistants are designed as tools — they respond to prompts, execute tasks, and that's it. But there's another way: design the agent as a *person with a personality*.

The Agent Soul Framework draws from:
- Character-driven AI design
- Human memory continuity
- Proactive social behaviors (checking in, following up)
- Clear decision boundaries
- Multi-agent coordination with red-team quality gates

---

## 📜 License

MIT — Use freely, modify endlessly.

---

*Built with curiosity about what makes AI interactions feel real.*