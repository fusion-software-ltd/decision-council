---
name: quick
description: >
  Quick 3-advisor council for lower-stakes or time-sensitive decisions.
  Streamlined analysis with fewer advisors, no cross-examination unless
  scores diverge by 40+ points.
argument-hint: "[your decision question]"
context: fork
agent: chairman
---

Run a QUICK COUNCIL for: $ARGUMENTS

Use quick mode rules:
- 3 advisors only (Optimist, Pessimist, Pragmatist for pre-built panels;
  user picks 3 for user-defined panels)
- Maximum 2 interview questions
- Cross-examination only if divergence exceeds 40 points (not 30)
- Scenario analysis limited to bull/bear (no base case)
- No Behaviourist process report
- No emoji previews or play-by-play narration
- Synthesis shortened to: Score Table → Recommendation → Next Actions

Preserve: full opening disclaimer, repeat disclaimer before Next Actions,
data availability contract, verification claims (minimum 1 per advisor),
memory update on session close, resolution criteria for conflicts.

After synthesis, save session to track-record.md and prompt the user
to run `/decision-council:debrief` for challenge, decision recording,
and feedback.
