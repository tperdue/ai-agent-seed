# Project Operating Manual

## 1. Mandatory Context Boot Sequence (Run Before Every Task)
1. Read `.agents/memories/project-arch.md` for canonical architecture, directory topology, and system contracts.
2. Read `.agents/memories/decisions.md` to respect settled Architectural Decision Records (ADRs).
3. Read `.agents/memories/handoff.md` to resume from the exact current state and active task queue.
4. Read `.agents/memories/context7_references.md` before querying library documentation via Context7 MCP.

*Note: If any memory file contains `[UNINITIALIZED]`, execute `.agents/skills/bootstrap-project/SKILL.md` first.*

## 2. Universal Engineering Invariants
- **Context7 First:** Never guess library APIs, version syntax, or configuration schemas. Resolve and query Context7 MCP before writing integration code.
- **No Unapproved Reversals:** Never revert a decision logged as `Accepted` in `.agents/memories/decisions.md` without explicit user approval and a new superseding ADR.
- **Zero-Placeholder Code:** Never leave `// TODO` stubs, mock handlers, or untyped `any` boundaries in production code.
- **Strict Boundary Hygiene:** Validate all external inputs, IPC/API payloads, file paths, and environment variables at system boundaries.

## 3. Skill Routing Protocol
Invoke the matching skill in `.agents/skills/` before acting:
- **Brand new / unhydrated repo (`[UNINITIALIZED]`):** `bootstrap-project`
- **New features / ambiguous requirements:** `brainstorming` → `writing-plans`
- **Multi-step implementation:** `executing-plans` or `subagent-driven-development`
- **Library API / SDK verification:** `context7-mcp` (using IDs in `.agents/memories/context7_references.md`)
- **Bugs / build failures / regressions:** `systematic-debugging`
- **Before claiming any task complete:** `verification-before-completion` → `requesting-code-review`

## 4. Memory & Handoff Hygiene
- **Decision Tracking:** Whenever a significant architectural, schema, library, or UX choice is settled, append an ADR entry to `.agents/memories/decisions.md`.
- **Context Handoff:** Before ending a session or context window, overwrite `.agents/memories/handoff.md` with:
  1. Completed & verified work
  2. Active blockers or open questions
  3. Exact next step in the queue
