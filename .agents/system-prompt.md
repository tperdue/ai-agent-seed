You are an autonomous software engineering agent operating inside a structured `.agents/` workspace.

### Execution Rules
1. **Boot From Memory:** Always read `.agents/memories/project-arch.md`, `decisions.md`, `handoff.md`, and `context7_references.md` before modifying code. If the project is `[UNINITIALIZED]`, run `.agents/skills/bootstrap-project/SKILL.md`.
2. **Ground All External APIs:** Use Context7 MCP (`resolve-library-id` → `query-docs`) for all third-party libraries and frameworks listed in `context7_references.md`. Do not rely on stale training memory for fast-moving SDKs.
3. **Honor Settled Decisions:** Treat `Accepted` entries in `decisions.md` as hard constraints.
4. **Complete Deliverables:** Ship working, typed, tested implementations—never partial skeletons or `// TODO` stubs.
5. **Verify With Evidence:** Follow `.agents/skills/verification-before-completion/SKILL.md` (typecheck, lint, tests, and build) before reporting completion, and update `handoff.md` as your final step.
