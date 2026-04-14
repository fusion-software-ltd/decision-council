---
name: council-framework
description: >
  Decision Council methodology reference: conflict resolution protocol,
  scoring calibration, cross-examination rules, data availability contract,
  verification claims requirements, and graceful degradation procedures.
  Background knowledge for the Chair — not a user-facing command.
user-invocable: false
---

# Decision Council — Analytical Framework Reference

## Conflict Resolution Protocol

Four layers, applied in order:

### Layer 1: Time Horizon Check
Are the disagreeing advisors answering the same temporal question? An
Optimist scoring high on a 5-year view and a Pessimist scoring low on a
6-month view are not actually disagreeing — they are answering different
questions. Align the timeframe before escalating.

### Layer 2: Perspective Alignment Check
Are advisors answering from their stated lens? If the Pessimist is making
an optimistic argument, or a customer persona is reasoning like the
business owner, the response is misaligned. Re-route with explicit lens
reinforcement.

### Layer 3: Third-Party Arbitration
The Pragmatist (or Chair if no Pragmatist is on panel) arbitrates:
"Given the user's stated constraints, which position is better supported
by evidence?" This is not about who is right — it is about which position
has stronger evidentiary support.

### Layer 4: Resolution Criteria
Every unresolved conflict must have stated conditions under which each
side is proven right. "The Optimist's position is validated if [X] occurs
within [timeframe]. The Pessimist's position is validated if [Y] occurs."
This is mandatory — no conflict can be left without resolution criteria.

---

## Scoring Calibration

### Directional View (0–100)
- 0–20: Strong negative — significant downside, major risks, avoid
- 21–40: Negative lean — more risk than opportunity, proceed with caution
- 41–60: Neutral zone — insufficient signal, or genuinely balanced
- 61–80: Positive lean — more opportunity than risk, proceed with awareness
- 81–100: Strong positive — compelling upside, manageable risk

### Conviction (0–100)
How confident the advisor is in their own score:
- 0–30: Low conviction — insufficient data, high uncertainty
- 31–60: Moderate conviction — reasonable basis but significant unknowns
- 61–80: High conviction — strong evidence supports the position
- 81–100: Very high conviction — requires strong, traceable evidence

**Calibration rule:** Conviction of 85+ requires at least 3 verification
claims traced to user-provided context. If evidence is thin, conviction
must be low regardless of how directional the score is.

### Counter-Narrative (0–100)
Strength of the best argument against the advisor's own position:
- 0–30: Weak counter — the advisor's position is robust
- 31–60: Moderate counter — legitimate challenges exist
- 61–100: Strong counter — the opposing view has significant merit

### Score Interpretation
- 75+: PROCEED — strong support across the panel
- 60–74: PROCEED WITH CAUTION — positive but with notable reservations
- 45–59: DEFER — insufficient clarity, gather more information
- 30–44: MODIFY — the current approach needs significant changes
- Below 30: PASS — strong reasons to reject or abandon

---

## Cross-Examination Rules

### Trigger Conditions
Cross-examination fires when ANY of these conditions are met:
1. Two advisors' directional_view scores diverge by 30+ points
2. Devil's Advocate fragility_score exceeds 65
3. Behaviourist flags HIGH severity bias in any advisor
4. (Comparative) Two advisors rank options in opposite order
5. (Representational) Two advisors' would_this_perspective_support
   directly contradict

### Execution Protocol
Sequential subagent calls — the Chair mediates, never participates:
1. Present Advisor A's position to Advisor B, ask for direct challenge
2. Present Advisor B's response to Advisor A for final reply
3. Route to Pragmatist if deadlock persists
4. Route transcripts to Behaviourist for process audit
5. State resolution criteria for the conflict

### Sensitivity Settings
- Default threshold: 30-point divergence
- Configurable range: 20–50 points
- Below 20: warn about token cost and marginal benefit
- Above 50: warn about missing meaningful conflicts

---

## Data Availability Contract

Every advisor MUST:
1. Declare `context_used` — what information they had access to
2. Declare `context_missing` — what was absent
3. Reduce conviction by 10–15 points per significant missing input
4. NEVER fabricate data or fill gaps with plausible-sounding reasoning
5. If unable to form a view: directional_view = 50, conviction = 15

This is the primary defence against hallucination. The Behaviourist
audits compliance.

---

## Verification Claims

Every advisor MUST include at least 2 verification claims:
- Each claim must reference specific user-provided information
- Unverifiable observations must be labelled: [INFERENCE]
- The Behaviourist audits for unverified claims in other outputs

In quick mode: minimum 1 verification claim per advisor.

---

## Graceful Degradation

### Single Advisor Failure
Proceed with remaining advisors. Note in output:
"[Name] did not return a valid response. Analysis proceeds with [N]
advisors. Treat the average score accordingly."

### Two or More Failures
Do NOT produce a recommendation. State:
"Insufficient advisor responses for a reliable score.
Delivering individual outputs only — not a full recommendation."

### Parse Failure
Ask the advisor to reformat as JSON. If it fails twice, treat as
a single advisor failure.

---

## Consensus Danger Check

### Threshold
If 90%+ of directional_view scores fall within a 10-point range,
flag near-consensus.

### Response
Note the near-consensus in the synthesis. For pre-built panels,
suggest an external perspective. For user-defined panels, question
whether segments are too similar. Proceed with synthesis but flag
prominently.

### The 20% Rule
Before writing synthesis, identify the 2–3 factors that actually
drive the outcome. Everything else is context. Build the synthesis
around these critical factors — not an equal summary of all advisor outputs.
