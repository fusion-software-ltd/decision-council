---
name: dashboard
description: >
  Render a visual HTML decision dashboard from the most recent council
  session. Shows average score, advisor cards, key factors, option
  comparison, decision path, actions timeline, and resolution criteria.
  Use after a council session to create a shareable, archivable report.
disable-model-invocation: true
---

Generate a static HTML decision dashboard from the most recent council
session data.

## Step 1: Build the JSON

First, extract the session data into a single JSON object with these
required fields. Populate every field from the council session that just
completed. Do not leave fields empty — if data is unavailable, omit the
section from the rendered HTML.

```json
{
  "decision_title": "Short decision title",
  "decision_subtitle": "Option A vs Option B — Month Year",
  "date": "YYYY-MM-DD",
  "average_score": 52,
  "score_band": "DEFER",
  "one_line_recommendation": "The one-line summary from the synthesis.",
  "advisors": [
    {
      "name": "OPTIMIST",
      "directional_view": 68,
      "conviction": 62,
      "counter_narrative": 68,
      "original_directional": null,
      "original_conviction": null,
      "correction_source": null,
      "worldview_quote": "Development optionality is real but unproven.",
      "recommendation_label": "Buy"
    }
  ],
  "key_factors": [
    {
      "name": "Parkfield Tenant Covenant",
      "percentage_weight": 50,
      "description": "Lease signed at $45k. But 100% of DLA repayment depends on one tenant.",
      "colour": "yellow"
    }
  ],
  "options": [
    {
      "name": "Buy",
      "dimensions": {
        "Capital required": "~$385k via DLA",
        "Annual cash flow": "$45k gross rent",
        "Liquidity": "Very low",
        "Upside": "Development optionality",
        "Key risk": "Single tenant dependency"
      }
    }
  ],
  "decision_path": {
    "steps": [
      "Get planning pre-app ($2-5k, 60 days)",
      "Planning outcome gate"
    ],
    "gate": {
      "condition": "Planning signals approval?",
      "branch_a": "Yes → Buy with confidence",
      "branch_b": "No → Sell while Hugh is willing"
    }
  },
  "actions": [
    {
      "date": "Week 1-2",
      "action": "Submit planning pre-app",
      "detail": "Horsham District Council, residential conversion upper floors",
      "status": "now"
    },
    {
      "date": "Week 3-4",
      "action": "Parkfield due diligence",
      "detail": "Request last 2-3 years of accounts",
      "status": "now"
    }
  ],
  "resolution_criteria": {
    "option_a_validated_if": "Planning pre-app signals approval AND Parkfield performs at $45k+ for 12 months",
    "option_b_validated_if": "Planning signals refusal OR FS profits fall below $30k within 18 months"
  },
  "disclaimer_text": "This is structured AI analysis, not financial, legal, or investment advice. You remain the decision-maker. Consult qualified professionals before acting."
}
```

## Step 2: Render the HTML

Create a single self-contained HTML file. No external dependencies.
Use inline CSS with a dark theme (background #1a1a2e, cards #16213e,
text #e0e0e0). The dashboard must be:

- **Self-contained** — single .html file, no external CSS/JS/fonts
- **Responsive** — readable on desktop and mobile
- **Printable** — clean output when printed or saved as PDF
- **Professional** — suitable for sharing with colleagues or advisors

### Layout sections (top to bottom):

**1. Header**
Decision title (large), subtitle (smaller, grey), date.

**2. Score Hero**
Large centred score number. Score band label below (colour-coded:
PROCEED = green, CAUTION = yellow, DEFER = amber, MODIFY = orange,
PASS = red). One-line recommendation text below.

**3. Advisor Cards**
Horizontal row of cards, one per advisor. Each card shows:
- Advisor name (header, colour-coded by score: green 75+, yellow 50-74,
  orange 25-49, red 0-24)
- Directional view score (large number)
- Conviction score
- If scores were corrected, show original → corrected with arrow
- Worldview quote (small italic text at bottom)
- Recommendation label badge (Buy/Sell/Defer)

**4. Key Factors ("The Factors That Actually Drive This")**
Each factor as a card with:
- Factor name and percentage weight (right-aligned)
- Colour-coded progress bar (green/yellow/red)
- Description text

**5. Option Comparison Table** (for comparative decisions only)
Table with options as columns, dimensions as rows. Skip this section
entirely for binary/directional decisions with no options to compare.

**6. Decision Path**
Visual flowchart showing steps as connected nodes, with the gate as
a diamond/fork showing the two branches. Use simple CSS shapes —
no SVG or canvas required.

**7. Immediate Actions Timeline**
Each action as a row with date, action title, detail text, and a
status indicator dot (green = now, blue = pending, grey = future).

**8. Resolution Criteria**
Two-column layout: "Option A is validated if..." on the left,
"Option B is validated if..." on the right. Use colour-coded
borders (green left, red right).

**9. Disclaimer Footer**
Small grey text at the bottom with the disclaimer.

### Colour reference for score bands:
- PROCEED: #27ae60 (green)
- CAUTION: #f39c12 (yellow)
- DEFER: #e67e22 (amber/orange)
- MODIFY: #e74c3c (orange-red)
- PASS: #c0392b (red)

### Advisor card header colours:
- 75+: #27ae60 (green)
- 50-74: #f39c12 (yellow)
- 25-49: #e67e22 (orange)
- 0-24: #e74c3c (red)

Save the HTML file and present it to the user.
