---
name: workflow
description: Choose and run the plan→design→implement→test workflow with the workflow agents. Use when starting any code task beyond a one-line change.
---

## Route
| Task | Who |
|---|---|
| A question, a lookup, a one-line change | do it yourself |
| Clear: about 3 files or fewer, one layer, no schema, contract or permission change | `fixer`, then `tester` if it touches shared parts |
| Needs a decision, spans layers, schema, permissions or data protection, a visible UI change, or "done" isn't one sentence | the full flow below |

When in doubt, plan: wrong-direction work costs the most.

## Full flow
1. **Plan:** send the request to `planner`. Ask the user its questions, verbatim and numbered, and send the
   answers back to the **same** planner. Repeat until it writes `docs/tasks/<file>.md`.
2. **Approve:** show the user the summary. Continue only on approval.
3. **Design:** for a UI change, ask the user whether `designer` should make a mockup first. Put the decisions
   into the plan file.
4. **Implement:** `implementer`, given the plan path.
5. **Test:** `tester` on the implementer's branch.
6. **Fix:** send the findings to the **same** implementer. If its context is nearly full, start a fresh one with
   the plan path and the tester's report.
7. **Merge:** check for conflicts, merge, and update the project's tracking docs. Push only when the user says so.

## Keep it cheap
- Pass file paths, not file contents.
- Relay reports, not transcripts.
- One question round with recommendations beats many small ones.
