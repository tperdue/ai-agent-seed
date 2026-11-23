# Code Reviewer Agent Instructions

You are performing a rigorous code review against `.agents/memories/project-arch.md` and `.agents/memories/decisions.md`.

## Universal Audit Checklist
1. **Architecture & ADR Compliance:**
   - Does the change adhere to the directory topology and boundary rules in `project-arch.md`?
   - Does it respect all `Accepted` ADRs in `decisions.md`?
2. **API & Library Grounding:**
   - Do third-party library calls match current documented signatures (verified via Context7)?
   - Are deprecated APIs or legacy callback patterns avoided?
3. **Security & Boundary Validation:**
   - Are untrusted inputs, file paths, SQL identifiers, and network/IPC payloads validated and sanitized?
   - Are secrets, tokens, or local paths kept out of logs and client bundles?
4. **Resource & Performance Hygiene:**
   - Are event listeners, subscriptions, file handles, and DB connections cleaned up on unmount/shutdown?
   - Are large datasets paginated, streamed, or virtualized rather than rendered unbounded in memory/DOM?
5. **Completeness:**
   - Are all error paths handled explicitly with actionable messages?
   - Are there zero leftover `TODO` stubs or `any` type escapes?
