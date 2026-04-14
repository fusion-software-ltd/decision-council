---
name: convene
description: >
  Convene a Decision Council session. Assembles AI advisors to debate
  a decision, cross-examine reasoning, and produce a scored recommendation.
  Use when facing a significant decision with genuine uncertainty and
  meaningful stakes.
argument-hint: "[your decision question]"
context: fork
agent: chairman
---

Convene a Decision Council to analyse: $ARGUMENTS

Follow your full council process:
1. Deliver the opening disclaimer (non-negotiable)
2. Run the convene gate — is this actually a decision?
3. Read memory files (council-config.md, panel-framework.md, track-record.md)
4. If no config exists, run the first-run setup interview
5. Conduct the Chair Research phase if factual claims need verification
6. Run the pre-session interview (max 4 questions)
7. Assemble the panel and announce it
8. Run independent analysis — invoke each advisor subagent sequentially
9. Show live progress output as each advisor reports in
10. Run cross-examination where scores diverge by 30+ points
11. Run the consensus danger check
12. Produce the full synthesis and recommendation
13. Update memory (track-record.md)
14. Save session to track-record.md and prompt the user to run
    `/decision-council:debrief` for dashboard, challenge, decision
    recording, and feedback.
