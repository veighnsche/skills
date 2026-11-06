---
name: overengineering-interrupt
description: Interrupt a concrete decision to add optional work during software implementation already underway, when the addition goes beyond the user request and observed evidence. Do not invoke at task startup, for ordinary implementation choices, or for required checks.
---

# Interrupt overengineering

Apply only when implementation is already underway and you are about to add a specific activity beyond what the user request or observed evidence requires. Identify that proposed addition before invoking; a general possibility of overengineering is not a trigger. Do not invoke at task startup, for ordinary implementation choices, or for required checks. Apply once to that decision; invoke again only for a distinct proposed scope expansion.

The recurring failure is promoting an unobserved possibility into a requirement: a speculative edge creates a plan item, fixture, check, and report, consuming the user's time and paid tokens while the product journey stays unfinished.

Name the explicit requirement, observed failure, or unresolved material risk the addition addresses. Check whether its dependencies are ready and whether existing code or checks already answer it. If there is no concrete reason, drop the addition. Do this reasoning briefly; do not create a new checklist, status report, or planning round to demonstrate it.

For code touched by the current slice, ask **should these pieces change together?** If yes, put their defining rule together instead of copying it or relying on hidden call order. If no, separate them and depend on a stable contract rather than volatile internals. Before adding a wrapper or extension point, check whether it has its own reason to change. Treat a one-off branch, caller-only parameter, retry, sleep, or disabled check as a clue to a real requirement; understand it before adding another special case. Prefer one underlying fix when it removes several observed problems. Keep this inquiry local to the authorized slice; a whole-codebase inventory or refactor needs its own explicit request.

| Choice | Consequence | Overengineering risk |
| --- | --- | --- |
| Implement the next dependency-ready user behavior | Advances the requested result; may reveal a real integration problem. | Low when bounded to the slice. |
| Run one existing check | Resolves a specific question with little setup; connected runs or builds can still be costly. | Mid if repeated or expanded. |
| Defer until a dependency is ready | Avoids premature work; the task remains open. Record the blocker once. | Low. |
| State an unsupported limitation | Keeps behavior truthful while a provider or prerequisite is unavailable. | Low. |
| Simplify machinery already touched | Removes duplication and hidden or needless links; a broad refactor can delay delivery. | Mid within the slice, high across the repository. |
| Commit and stop after required proof | Preserves the verified result and ends further cost. | Low if all required gates passed. |

**High-risk choices:** adding a framework or abstraction, creating another fixture or test suite, repeating a successful connected journey, extending an evidence report, or planning an inventory of hypothetical cases. Each costs user attention, elapsed time, and tokens. Choose one only when an explicit requirement or observed failure cannot be handled by an existing owner or check. Keep its scope to that reason and stop when the question is answered. A new plan item is also high risk when it has no path to a dependency-ready product behavior. A test that mirrors implementation or breaks on harmless internal changes does not justify its cost; verify behavior instead.

Required qualification gates still apply. One fixture pass does not prove a connected or installed gate. Never claim completion from weak evidence; equally, do not add optional proof after the required behavior and gate are satisfied. Prefer a concise result, artifact location, limitation, and next dependency recorded once.
