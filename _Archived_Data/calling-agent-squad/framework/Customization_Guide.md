# How to Customize Your Agent Squad

This framework is designed to be modular. You can easily rename agents or change their personalities while keeping the core logic intact.

## 1. Renaming Agents
To rename an agent (e.g., from `Reviewer` to `Copper`), simply update the following:
- **File Name**: Rename `framework/Reviewer.md` to `framework/Copper.md`.
- **Identity Prompt**: Update the `IDENTITY` section within that file.
- **Main's Soul**: Update `framework/Main.md` so the instructions point to your new agent name.

## 2. Dynamic Personalities
If you want a specific "tone" (e.g., Aggressive vs. Diplomatic), you can swap out the `IDENTITY` section while keeping the `SOUL` (the core logic/SOP) the same.

## 3. Adding Niche Experts
Create a new file in `framework/` following the `SP-Expert.md` template to inject specific constraints or knowledge into your squad.
