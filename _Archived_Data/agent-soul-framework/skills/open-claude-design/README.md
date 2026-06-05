# Open-Claude-Design

A meta-prompt engineering skill that encodes Anthropic's Claude Design principles.

## What It Does

Turns any AI into a rigorous prompt designer. Use it to:
- Design new prompts from scratch
- Refactor existing prompts with structural discipline
- Apply anti-AI-slop standards to any output

## Core Framework

```
Layer 1: PROHIBITIONS (top — hard walls, never negotiate)
Layer 2: SPO — Subject, Predicate, Object (core identity + logic)
Layer 3: FORMAT + SKILLS + REFERENCES (bottom — technical specs)
```

The key insight: **most prompts fail at the design level, not the execution level.**

## Trigger

```
design prompt for [role/task]  → Generate a full prompt
apply claude design to [text]  → Refactor an existing prompt
improve prompt [name]           → Identify weaknesses
```

## Key Principles

### Prohibitions First
Write what the AI should **never do** before what it should do. This is the most commonly missing element in most prompts.

### Question-Driven Predicate
Before executing, the AI should ask:
- What output format?
- What fidelity level?
- How many variants?
- What constraints?
- Deadline?

### Anti-AI-Slop
Remove: placeholder text, 凑数版块, aggressive gradients, overused fonts (Inter/Roboto/Arial), emoji as icons, decorative non-data stats.

## Files

- `SKILL.md` — Full skill definition
- `prompts/` — Prompts designed or improved by this skill

## Source

Principles extracted from Anthropic's internal Claude Design system prompt, shared with permission for educational use.
