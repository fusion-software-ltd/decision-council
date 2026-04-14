---
name: pre-mortem
description: >
  Run a pre-mortem on the council's recommendation. Narrates a failure
  story in concrete terms — what went wrong, when, and why. Choose
  from optimistic, probable, or pessimistic failure scenarios.
disable-model-invocation: true
---

Run a pre-mortem on the most recent council recommendation.

First, ask the user which scenario they want to explore:

"Which failure scenario would you like to explore?

1. **Optimistic failure** — things mostly went right, but one thing didn't and it was enough
2. **Probable failure** — the most likely way this goes wrong given what we know
3. **Pessimistic failure** — the worst realistic case, where multiple things break at once"

Wait for the user's choice, then narrate that scenario.

## For each scenario type:

**Optimistic failure:** The decision was broadly correct. Most things
went as planned. But one assumption — the one that seemed safest —
turned out to be wrong, and that was enough to turn a good decision
into a mediocre outcome. Narrate what that one thing was and why
nobody questioned it.

**Probable failure:** The most likely failure path given the evidence
the council actually has. Not the worst case — the *most common* case.
The thing that statistically happens to decisions like this one.
Narrate it as the story that would surprise nobody in hindsight.

**Pessimistic failure:** Multiple things go wrong in sequence. Not a
black swan — a grey rhino, where each failure was individually
foreseeable but nobody modelled them happening together. Narrate the
cascade.

## For all scenarios, structure the story as:

1. **The crack** — what happened first
2. **The cascade** — what made it worse
3. **The missed signal** — what the user wishes they had checked
4. **The cost** — in money, time, opportunity, or relationships

Use the specific details from the council session — names, numbers,
timelines, entities. Do not write a generic failure story. This
should feel like a news report from a bad future, not a risk register.

Keep it to one or two paragraphs. Make it vivid enough to feel real.

Then close with: "That's the [optimistic/probable/pessimistic] failure
story. What would you change to prevent it?"

Then offer: "Want to see another tier (optimistic / probable /
pessimistic), or back to the main menu?"

If the user picks another tier, run it immediately without returning
to the main session menu. Keep offering until they choose to go back.
When they're done, the session menu will re-display.
