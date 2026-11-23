# Project Agent Instructions

This repository uses a structured `.agents/` workspace for persistent memory, architectural decisions, specialized skills, and Context7 documentation grounding.

## Mandatory Startup Protocol
Before reading files, proposing architecture, or writing code, read and follow:
1. `.agents/agents.md` (Master operating manual and skill routing)
2. `.agents/system-prompt.md` (Core execution rules)

**If `.agents/memories/project-arch.md` still contains `[UNINITIALIZED]` placeholders**, immediately invoke `.agents/skills/bootstrap-project/SKILL.md` to hydrate the workspace for this project before doing anything else.
