---
name: status
description: >
  Show current Decision Council configuration and advisor track record.
  Displays panel composition, sessions completed, and
  per-advisor accuracy.
disable-model-invocation: true
---

Read and display the current contents of the Decision Council memory files:

1. **council-config.md** — Panel configuration:
   - Domain and primary tension
   - Panel composition (which advisors, what type)
   - Cross-examination sensitivity threshold
   - Default decision type

2. **track-record.md** — Advisor performance:
   - Total sessions completed
   - Per-advisor accuracy table
   - Recent session history

3. **panel-framework.md** — Framework settings:
   - Scoring scale
   - Conflict resolution protocol
   - Consensus danger threshold

Present as a clear, readable summary. If any files are missing, note
which ones and suggest running `/decision-council:convene` to initialise.
